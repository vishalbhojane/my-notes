```js
const asyncBatchProcessing = async (tasks,batchSize) =>{
     let activeTasks = [];
     
     for(let i = 0;i<tasks.length;i++){
         if(activeTasks.length >= batchSize){
             await Promise.race(activeTasks);
         }
         const currentTask = tasks[i](i).then((data) =>{
              console.log(data);
              activeTasks.splice(activeTasks.indexOf(tasks[i]),1);
         }).catch((err) =>{
             activeTasks.splice(activeTasks.indexOf(tasks[i]),1);
         });
         
         activeTasks.push(currentTask);
     }
}
```

Usage

```js
const p1 = (idx) =>{
    return new Promise((resolve,reject) =>{
         setTimeout(() =>{
             resolve(`p${idx} settled`)
         }, 1000);
    })
}

const tasks = [p1,p1,p1,p1,p1,p1,p1,p1,p1,p1];

asyncBatchProcessing(tasks,3)
```