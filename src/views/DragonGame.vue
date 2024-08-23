<template>
    <div id="game">
      <div id="stats">
        <span class="stat">XP: <strong><span>{{ xp }}</span></strong></span>
        <span class="stat">Health: <strong><span>{{ health }}</span></strong></span>
        <span class="stat">Gold: <strong><span>{{ gold }}</span></strong></span>
      </div>
      <div id="controls">
        <button @click="buttonFunctions[0]">{{ buttonTexts[0] }}</button>
        <button @click="buttonFunctions[1]">{{ buttonTexts[1] }}</button>
        <button @click="buttonFunctions[2]">{{ buttonTexts[2] }}</button>
      </div>
      <div v-if="monsterStatsVisible" id="monsterStats">
        <span class="stat">Monster Name: <strong><span>{{ monsterName }}</span></strong></span>
        <span class="stat">Health: <strong><span>{{ monsterHealth }}</span></strong></span>
      </div>
      <div id="text">
        {{ text }}
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Initial game state
  const xp = ref(0);
  const health = ref(100);
  const gold = ref(50);
  const currentWeapon = ref(0);
  const fighting = ref(null);
  const monsterHealth = ref(null);
  const inventory = ref(["stick"]);
  
  const buttonTexts = ref(["Go to store", "Go to cave", "Fight dragon"]);
  const buttonFunctions = ref([goStore, goCave, fightDragon]);
  
  const monsterStatsVisible = ref(false);
  const monsterName = ref("");
  const monsterHealthText = ref("");
  const text = ref("");
  
  const weapons = [
    { name: 'stick', power: 5 },
    { name: 'dagger', power: 30 },
    { name: 'claw hammer', power: 50 },
    { name: 'sword', power: 100 }
  ];
  const monsters = [
    { name: "slime", level: 2, health: 15 },
    { name: "fanged beast", level: 8, health: 60 },
    { name: "dragon", level: 20, health: 300 }
  ];
  const locations = [
    { name: "town square", "button text": ["Go to store", "Go to cave", "Fight dragon"], "button functions": [goStore, goCave, fightDragon], text: "You are in the town square. You see a sign that says \"Store\"." },
    { name: "store", "button text": ["Buy 10 health (10 gold)", "Buy weapon (30 gold)", "Go to town square"], "button functions": [buyHealth, buyWeapon, goTown], text: "You enter the store." },
    { name: "cave", "button text": ["Fight slime", "Fight fanged beast", "Go to town square"], "button functions": [fightSlime, fightBeast, goTown], text: "You enter the cave. You see some monsters." },
    { name: "fight", "button text": ["Attack", "Dodge", "Run"], "button functions": [attack, dodge, goTown], text: "You are fighting a monster." },
    { name: "kill monster", "button text": ["Go to town square", "Go to town square", "Go to town square"], "button functions": [goTown, goTown, easterEgg], text: 'The monster screams "Arg!" as it dies. You gain experience points and find gold.' },
    { name: "lose", "button text": ["REPLAY?", "REPLAY?", "REPLAY?"], "button functions": [restart, restart, restart], text: "You die. ☠️" },
    { name: "win", "button text": ["REPLAY?", "REPLAY?", "REPLAY?"], "button functions": [restart, restart, restart], text: "You defeat the dragon! YOU WIN THE GAME! 🎉" },
    { name: "easter egg", "button text": ["2", "8", "Go to town square?"], "button functions": [pickTwo, pickEight, goTown], text: "You find a secret game. Pick a number above. Ten numbers will be randomly chosen between 0 and 10. If the number you choose matches one of the random numbers, you win!" }
  ];
  
  function update(location) {
    monsterStatsVisible.value = false;
    buttonTexts.value = location["button text"];
    buttonFunctions.value = location["button functions"];
    text.value = location.text;
  }
  
  function goTown() {
    update(locations[0]);
  }
  
  function goStore() {
    update(locations[1]);
  }
  
  function goCave() {
    update(locations[2]);
  }
  
  function buyHealth() {
    if (gold.value >= 10) {
      gold.value -= 10;
      health.value += 10;
    } else {
      text.value = "You do not have enough gold to buy health.";
    }
  }
  
  function buyWeapon() {
    if (currentWeapon.value < weapons.length - 1) {
      if (gold.value >= 30) {
        gold.value -= 30;
        currentWeapon.value++;
        let newWeapon = weapons[currentWeapon.value].name;
        text.value = "You now have a " + newWeapon + ".";
        inventory.value.push(newWeapon);
        text.value += " In your inventory you have: " + inventory.value;
      } else {
        text.value = "You do not have enough gold to buy a weapon.";
      }
    } else {
      text.value = "You already have the most powerful weapon!";
      buttonTexts.value[1] = "Sell weapon for 15 gold";
      buttonFunctions.value[1] = sellWeapon;
    }
  }
  
  function sellWeapon() {
    if (inventory.value.length > 1) {
      gold.value += 15;
      let currentWeaponName = inventory.value.shift();
      text.value = "You sold a " + currentWeaponName + ".";
      text.value += " In your inventory you have: " + inventory.value;
    } else {
      text.value = "Don't sell your only weapon!";
    }
  }
  
  function fightSlime() {
    fighting.value = 0;
    goFight();
  }
  
  function fightBeast() {
    fighting.value = 1;
    goFight();
  }
  
  function fightDragon() {
    fighting.value = 2;
    goFight();
  }
  
  function goFight() {
    update(locations[3]);
    monsterHealth.value = monsters[fighting.value].health;
    monsterStatsVisible.value = true;
    monsterName.value = monsters[fighting.value].name;
    monsterHealthText.value = monsterHealth.value;
  }
  
  function attack() {
    text.value = "The " + monsters[fighting.value].name + " attacks.";
    text.value += " You attack it with your " + weapons[currentWeapon.value].name + ".";
    health.value -= getMonsterAttackValue(monsters[fighting.value].level);
    if (isMonsterHit()) {
      monsterHealth.value -= weapons[currentWeapon.value].power + Math.floor(Math.random() * xp.value) + 1;
    } else {
      text.value += " You miss.";
    }
    if (health.value <= 0) {
      lose();
    } else if (monsterHealth.value <= 0) {
      fighting.value === 2 ? winGame() : defeatMonster();
    }
    if (Math.random() <= .1 && inventory.value.length !== 1) {
      text.value += " Your " + inventory.value.pop() + " breaks.";
      currentWeapon.value--;
    }
  }
  
  function getMonsterAttackValue(level) {
    const hit = (level * 5) - (Math.floor(Math.random() * xp.value));
    return hit > 0 ? hit : 0;
  }
  
  function isMonsterHit() {
    return Math.random() > .2 || health.value < 20;
  }
  
  function dodge() {
    text.value = "You dodge the attack from the " + monsters[fighting.value].name;
  }
  
  function defeatMonster() {
    gold.value += Math.floor(monsters[fighting.value].level * 6.7);
    xp.value += monsters[fighting.value].level;
    update(locations[4]);
  }
  
  function lose() {
    update(locations[5]);
  }
  
  function winGame() {
    update(locations[6]);
  }
  
  function restart() {
    xp.value = 0;
    health.value = 100;
    gold.value = 50;
    currentWeapon.value = 0;
    inventory.value = ["stick"];
    goTown();
  }
  
  function easterEgg() {
    update(locations[7]);
  }
  
  function pickTwo() {
  pick(2);
}

function pickEight() {
  pick(8);
}

function pick(guess) {
  const numbers = [];
  while (numbers.length < 10) {
    numbers.push(Math.floor(Math.random() * 11));
  }
  text.value = "You picked " + guess + ". Here are the random numbers:\n";
  for (let i = 0; i < 10; i++) {
    text.value += numbers[i] + "\n";
  }
  if (numbers.indexOf(guess) !== -1) {
    text.value += "Right! You win 20 gold!";
    gold.value += 20;
  } else {
    text.value += "Wrong! You lose 10 health!";
    health.value -= 10;
    if (health.value <= 0) {
      lose();
    }
  }
}
</script>

<style>
body {
  background-color: #0a0a23;
}

#text {
  background-color: #0a0a23;
  color: #ffffff;
  padding: 10px;
}

#game {

  max-width: 500px;
  max-height: 400px;
  background-color: #ffffff;
  color: #000000;
  margin: 200px auto 0px;
  padding: 10px;
}

#controls,
#stats {
  border: 1px solid #0a0a23;
  padding: 5px;
  color: #0a0a23;
}

#monsterStats {
  display: none;
  border: 1px solid #0a0a23;
  padding: 5px;
  color: #ffffff;
  background-color: #c70d0d;
}

.stat {
  padding-right: 10px;
}

button {
  cursor: pointer;
  color: #0a0a23;
  background-color: #feac32;
  background-image: linear-gradient(#fecc4c, #ffac33);
  border: 3px solid #feac32;
}
</style>
