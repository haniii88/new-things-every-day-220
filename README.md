```javascript
function dailyLog220() {
  const employees = [
    { name: "Alex", tasks: 42, quality: 95 },
    { name: "Sarah", tasks: 38, quality: 98 },
    { name: "Michael", tasks: 50, quality: 85 },
    { name: "Emma", tasks: 35, quality: 92 },
    { name: "Daniel", tasks: 45, quality: 88 },
  ];

  const maxTasks = Math.max(
    ...employees.map(employee => employee.tasks)
  );

  const ranked = employees.map(employee => {
    const taskScore = (employee.tasks / maxTasks) * 100;
    const score = taskScore * 0.4 + employee.quality * 0.6;

    return {
      ...employee,
      score: Number(score.toFixed(2)),
    };
  }).sort((a, b) => b.score - a.score);

  const averageScore =
    ranked.reduce((sum, employee) => sum + employee.score, 0) /
    ranked.length;

  console.log("=== Employee Performance Report ===");
  console.log(`Team Members: ${ranked.length}`);
  console.log(`Average Score: ${averageScore.toFixed(2)}/100`);

  console.log("\n=== Performance Rankings ===");

  ranked.forEach((employee, index) => {
    console.log(
      `${index + 1}. ${employee.name} — ${employee.score}/100`
    );
  });

  console.log(`\n🏆 Top Performer: ${ranked[0].name}`);
  console.log("✅ Performance analysis completed!");
}

dailyLog220();
```
