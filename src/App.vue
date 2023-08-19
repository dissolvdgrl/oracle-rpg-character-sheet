<script setup lang="ts">
  const abilities = ["Strength", "Agility", "Stamina", "Intellect" , "Wits", "Charisma"];
  const attributes = ["Health Points", "Armor", "Momentum", "Experience"];
  const skills = [
    { id: 1, name: "Acrobatics", ability: "Agi" },
    { id: 2, name: "Athletics", ability: "Str" },
    { id: 3, name: "Fighting", ability: "Str" },
    { id: 4, name: "Hacking", ability: "Int" },
    { id: 5, name: "Healing", ability: "Int" },
    { id: 6, name: "Intimidation", ability: "Str" },
    { id: 7, name: "Investigation", ability: "Wit" },
    { id: 8, name: "Knowledge", ability: "Int" },
    { id: 9, name: "Power", ability: "Int" },
    { id: 10, name: "Perception", ability: "Wit" },
    { id: 11, name: "Persuasion", ability: "Chr" },
    { id: 12, name: "Shooting", ability: "Agi" },
    { id: 13, name: "Stealth", ability: "Agi" },
    { id: 14, name: "Survival", ability: "Wit" },
    { id: 15, name: "Taunt", ability: "Chr" },
    { id: 16, name: "Thievery", ability: "Agi" }
  ];
</script>

<template>
  <div class="mx-auto max-w-2xl grid grid-cols-2 gap-8 my-16">
    <!-- Character Name -->
    <div class="flex flex-col">
      <h2 class="font-bold text-xl">Character Name</h2>
      <input type="text" name="characterName" class="border border-gray-200 rounded-md text-2xl p-2">
    </div>

    <!-- Character Concept -->
    <div class="flex flex-col">
      <h2 class="font-bold text-xl">Concept</h2>
      <input type="text" name="characterName" class="border border-gray-200 rounded-md text-2xl p-2">
    </div>
    <hr class="col-span-2">
    <!-- Ability Scores -->
    <div class="col-span-2 grid grid-cols-2 gap-8">
      <div class="grid grid-cols-3 gap-8">
        <div class="flex flex-col" v-for="ability in abilities">
          <label class="font-bold">{{ ability }}</label>
          <input type="number" :name="ability.toLowerCase()" min="1" value="1" class="border border-gray-200 rounded-md p-2">
        </div>
      </div>
      <div class="grid grid-cols-2 gap-8">
        <div class="flex flex-col" v-for="attribute in attributes">
          <label class="font-bold">{{ attribute }}</label>
          <input type="number" :name="attribute.toLowerCase().split(' ').join('')" min="0" class="border border-gray-200 rounded-md p-2">
        </div>
      </div>
    </div>

    <hr class="col-span-2">

    <!-- Skills -->
    <div class="col-span-2">
      <h2 class="font-bold text-xl">Skills</h2>
      <div class="grid grid-cols-4 gap-4">
        <div class="col-span-2"></div>
        <div class="text-xs text-center font-bold">Skill Total</div>
        <div class="text-xs text-center font-bold">Difficulty</div>
        <div v-for="skill in skills" class="grid grid-cols-4 gap-4 col-span-4">
          <div class="flex gap-2 items-stretch justify-between col-span-2">
            <label class="font-bold self-center">{{ skill.name }}</label>
            <input type="number" :name="`${skill.name.toLowerCase()}Value`" min="0" class="border border-gray-200 rounded-md w-1/3">
          </div>
          <div class="flex gap-2 items-stretch justify-between">
            <label class="font-bold text-4xl">&plus;</label>
            <input type="number" :name="`${skill.name.toLowerCase()}SkillTotal`" min="0" class="border border-gray-200 rounded-md w-full">
          </div>
          <div class="flex gap-2 items-stretch justify-between">
            <input type="number" :name="`${skill.name.toLowerCase()}Difficulty`" min="0" class="border border-gray-200 rounded-md w-full">
          </div>
        </div>
      </div>
    </div>

    <hr class="col-span-2">

    <!-- Talents, Powers & Success Die -->
    <div class="col-span-2 grid grid-cols-2 gap-8">
      <div>
        <h2 class="font-bold text-xl">Talents</h2>
        <textarea class="border border-gray-200 rounded-md p-2 w-full" name="talents"></textarea>
      </div>
      <div>
        <h2 class="font-bold text-xl">Talents</h2>
        <textarea class="border border-gray-200 rounded-md p-2 w-full" name="powers"></textarea>
      </div>
      <div class="col-span-2">
        <h2 class="font-bold text-xl">Success Die</h2>
        <input type="number" name="successDie" min="0" class="border border-gray-200 rounded-md p-2 w-full">
      </div>
    </div>
  </div>
</template>
