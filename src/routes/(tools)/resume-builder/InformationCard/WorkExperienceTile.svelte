<script lang="ts">
 import { WorkExpStore } from "./workExp";
 import WorkExperienceForm from "./WorkExperienceForm.svelte";
 let IsEditing=false;
 function toogleform(){
  IsEditing=!IsEditing;
 }
 export let idfordetail: number;
</script>
  <div class="bg-gray-400 rounded-2xl font-sans flex justify-between mb-4">
    <div class="px-5 py-5 align-middle">
      <div class=" font-bold pb-1 flex">{$WorkExpStore[idfordetail].company_name}<p class="text-gray-600 font-medium">  | {$WorkExpStore[idfordetail].designation}</p>
      </div>
      <ul class="text-gray-800 list-disc pl-5">
        <li>{$WorkExpStore[idfordetail].discription_1}</li>
        <li>{$WorkExpStore[idfordetail].discription_2}</li>
      </ul>      
      <div class="text-gray-500 text-sm">{$WorkExpStore[idfordetail].start_date} - {$WorkExpStore[idfordetail].end_date}</div>
    </div>
    
    <div class="px-5 py-5">
      <button on:click={toogleform} class="flex items-center rounded-xl border-2 border-gray-800 p-1 pl-3 pr-3 font-medium">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="mr-2 h-4 w-4">
          <path d="M21.731 2.269a2.625 2.625 0 00-3.712 0l-1.157 1.157 3.712 3.712 1.157-1.157a2.625 2.625 0 000-3.712zM19.513 8.199l-3.712-3.712-12.15 12.15a5.25 5.25 0 00-1.32 2.214l-.8 2.685a.75.75 0 00.933.933l2.685-.8a5.25 5.25 0 002.214-1.32L19.513 8.2z" />
        </svg>
        <span>Edit</span>
      </button>
    </div>    
  </div>
  {#if IsEditing}
    <WorkExperienceForm onCancel={toogleform} idtoadd={idfordetail}/>
  {/if}