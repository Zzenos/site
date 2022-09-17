<template>
	<h1>drag-test-page</h1>
  <div id="wrapper" class="wrppaer">
    <div class="draggable-container">
      <div id="draggable" class="draggable" draggable="true"></div>
    </div>
    <div id="droppable" class="droppable"></div>
  </div>
</template>
  
<script setup lang="ts">
  import {nextTick} from 'vue'

  nextTick(() => {
    const draggable = document.getElementById('draggable')
    const droppable = document.getElementById('droppable')

    const handleDragStart = (e: any) => {
      e.dataTransfer.setData('text/plain', e.target.id)
    }
    const handleDragover = (e: any) => {
      e.preventDefault()
      droppable.classList.add('dragover')
    }
    const handleDragLeave = (e: any) => {
      droppable.classList.remove('dragover')
    }
    const handleDrop = (e: any) => {
      e.preventDefault()
      const draggableId = e.dataTransfer.getData('text/plain')
      droppable.appendChild(document.getElementById(draggableId))
      droppable.classList.add('droped')
    }
    
    draggable.addEventListener('dragstart', handleDragStart)
    droppable.addEventListener('dragover', handleDragover)
    droppable.addEventListener('dragleave', handleDragLeave)
    droppable.addEventListener('drop', handleDrop)

    // =============================================

    // const wrap = document.getElementById('wrapper')

    // const moving = (e: any) => {
    //   console.log('moving', e)
    //   // console.log(e.pageX, e.pageY, draggable.offsetLeft, draggable.offsetTop)

    // }
    // const mouseup = () => {
    //   console.log('wrap--mouse-up')
    //   wrap.removeEventListener('mousemove', moving)
    // }
    // wrap.addEventListener('mousemove', moving)
    // wrap.addEventListener('mouseup', mouseup)

    // const ctnLeft = droppable.offsetLeft
    // const ctnTop = droppable.offsetTop
    // const mousedown = (e: any) => {
    //   // e.target.getBoundingClientRect()
    //   console.log(ctnLeft, ctnTop, e.pageX, e.pageY)

    //   const l = e.pageX - ctnLeft - draggable.offsetLeft
    //   const t = e.pageY - ctnTop - draggable.offsetTop
    //   document.addEventListener('mousemove', (e: any) => {
    //     // console.log(e)
    //     draggable.style.left = e.pageX - ctnLeft - l + 'px'
    //     draggable.style.top = e.pageX - ctnLeft - t + 'px'
        
    //   }, false)
    // }
    // const mousedown = () => {
    //   console.log('draggable--mouse-down')
    //   wrap.addEventListener('mousemove', () => {
    //     console.log(111)
        
    //   })
    // }
    // draggable.addEventListener('mousedown', mousedown)

  })

</script>
<style lang="scss">
* {
  box-sizing: border-box;
}
.wrppaer {
  height: 800px;
  width: 100%;
  margin-top: 50px;
  background: hsl(0edg, 0%, 10%);
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;

 
  .draggable-container {
    width: 25vw;
    height: 25vh;
    margin-right: 80px;
  }
  .draggable {
    width: 25vw;
    height: 25vh;
    background-color: #00d9ff;
    border-radius: 4px;
    position: absolute;
  }
 
  .droppable {
    width: 30vw;
    height: 30vh;
    border: 8px dashed #00d9ff;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 4px;

    &::before {
      content: '请拖放到此区域';
      // display: block;
      position: absolute;
      color: hsl(0, 0%, 30%);
    }

    &.dragover {
      border: 8px dashed #ffae00;
    }
    &.droped {
      border: 8px dashed #48ff00;
      &::before {
        z-index: -1;
      }
    }
  }
}
</style>