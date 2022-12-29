<template>
  <div class="grid grid-cols-12 w-100 px-2">
    <div class="col-span-9">
      <div 
      v-for="(week, index) in weekNum" :key="'week' + index" 
      ref="weekBoard"
      class="my-2 border-2 border-black"
      @drop="isStartDrag=!isStartDrag;onDrop(week);dragOverStyle($event);"
      @dragover.prevent
      @dragenter.prevent
      >
        <h2>{{ week }}</h2>
        <div class="flex flex-wrap">
          <div v-for="(data, i) in beShowedData[week]" :key="data.className + i"
        >
          <ShowCard 
          :card-data="data"
          :draggable="isDragAble"
          :start-drag="isStartDrag"
          @dragstart="isStartDrag=!isStartDrag;startDrag($event,data,i,week);"
          @dragenter.self="dragEnterMove(i);dragOverStyle($event)"
          @dragleave="dragLeaveStyle($event)"
          />
        </div>
        </div>
      </div>
    </div>

    <div 
    class="col-span-3 border-2 border-black ml-1 my-2 bg-purple-400"
    ref="pileBoard"
    @drop="isStartDrag=!isStartDrag;onDrop(week);dragOverStyle($event);"
    @dragover.prevent
    @dragenter.prevent
    >
    <h2>pile</h2>
      <div v-for="(data, i) in pileData" :key="data.className + i">
        <ShowCard 
        :card-data="data"
        :draggable="isDragAble"
        :start-drag="isStartDrag"
        @dragstart="isStartDrag=!isStartDrag;startDrag($event,data,i,week);"
        @dragenter.self="dragEnterMove(i);dragOverStyle($event)"
        @dragleave="dragLeaveStyle($event)"
        />
      </div> 
      
    </div>
  </div>


</template>


<script setup>
import { ref } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";
import ShowCard from "./components/ShowCard.vue";
const isStartDrag = ref(false);
const pileData = ref([
  {
    className: 'refactor',
    classType: 'Technical',
    classDate: '',
    speaker: ['Bell'],
    isClassDone: false,
    isSKADone: false,
    isPile: true,
  },
  {
    className: 'MVC',
    classType: 'Technical',
    classDate: '',
    speaker: ['Bell', 'cindy'],
    isClassDone: false,
    isSKADone: false,
    isPile: true,
  }
])
const beShowedData =ref( {
  week1: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week2: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week3: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week4: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week5: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week6: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week7: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week8: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week9: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week10: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week11: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week12: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
  week13: [
    {
      className: 'refactor',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    },
    {
      className: 'MVC',
      classType: 'Technical',
      classDate: '',
      speaker: ['Bell', 'cindy'],
      isClassDone: false,
      isSKADone: false,
      isPile: false,
    }
  ],
})
const isDragAble = ref(true);
const weekNum = ref(Object.keys(beShowedData.value));
let tempData=
  { tempInfo:{},
    tempWeek:null,
    tempIndex:null
};
let dropIndex = null;
function startDrag(e,data,index,week){
  console.log("drag",isStartDrag.value)
  e.dataTransfer.dropEffect = 'move';
  e.dataTransfer.effectAllowed = 'move';
  tempData.tempInfo = data;
  tempData.tempWeek = week;
  tempData.tempIndex = index;
  
}
function writeDropIndex(index){
  dropIndex = index;
}
function dragEnterMove(index){
  writeDropIndex(index);
}
function spliceDragData(){
  if(tempData.tempWeek){
    beShowedData.value[tempData.tempWeek].splice(tempData.tempIndex,1);
  } else{
    pileData.value.splice(tempData.tempIndex,1);
  }
}
function writeDragData(week){
  if(week){
    tempData.tempInfo.isPile = false;
    beShowedData.value[week].splice(dropIndex,0,tempData.tempInfo);
  } else{
    tempData.tempInfo.isPile = true;
    pileData.value.splice(dropIndex,0,tempData.tempInfo);
  }
}
function onDrop(week){
  spliceDragData();
  writeDragData(week);
  tempData = { 
    tempInfo:{},
    tempWeek:null,
    tempIndex:null
};
  dropIndex = null;
  saveDataToLoclStorage()
}
function dragLeaveStyle(e){
  e.target.classList.remove("dragOverStyle");
 }
 function dragOverStyle(e){
  e.target.classList.add("dragOverStyle");
  
 }
 const isbooleantest = ref(true)
function saveDataToLoclStorage(){
  localStorage.setItem('pileData',JSON.stringify(pileData.value));
  localStorage.setItem('beShowedData',JSON.stringify(beShowedData.value));
}
function checkLocaStorageAndReplace(){
  if(!JSON.parse(localStorage.getItem('pileData'))){
    localStorage.setItem('pileData',JSON.stringify(pileData.value));
  }else{
    pileData.value = JSON.parse(localStorage.getItem('pileData'));
  }
  if(!JSON.parse(localStorage.getItem('beShowedData'))){
    localStorage.setItem('beShowedData',JSON.stringify(beShowedData.value));
  }else{
    beShowedData.value = JSON.parse(localStorage.getItem('beShowedData'));
  }
}
checkLocaStorageAndReplace();

onMounted(() => {

})
</script>



<style scoped>
.dragOverStyle {
    opacity: 0.7;
}
</style>
