```javascript
const asyncBatchProcessing = async (tasks, batchSize) => {
    const results = [];
    let activeTasks = [];

    for (let i = 0; i < tasks.length; i++) {
        if (activeTasks.length >= batchSize) {
            await Promise.race(activeTasks);
        }

        const currentTask = tasks[i](i).then((data) => {
            console.log(data);
            results.push(data);
            activeTasks = activeTasks.filter(t => t !== currentTask);
        }).catch((err) => {
            console.error(`Task ${i} failed:`, err);
            results.push(null);
            activeTasks = activeTasks.filter(t => t !== currentTask);
        });

        activeTasks.push(currentTask);
    }

    // Wait for any remaining tasks
    await Promise.all(activeTasks);

    return results;
};
```

Usage

```javascript
const p1 = (idx) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(`p${idx} settled`);
        }, 1000);
    });
};

const tasks = Array(10).fill(p1);

asyncBatchProcessing(tasks, 3).then(results => {
    console.log("All tasks completed. Results:", results);
})
```