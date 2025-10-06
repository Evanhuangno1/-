# -
适用于monad社区识别器

在F12控制台上面输入下面代码就可以了，pause = true → 暂停

pause = false → 继续运行


你通过在控制台输入：


// === 智能自动点击 "Yes" / "Keep playing" 循环脚本（含暂停功能） ===

let pause = false;           // 控制开关，true = 暂停，false = 继续
const interval = 1000;       // 每次检测/点击间隔 (毫秒)

function autoClick() {
  if (pause) {
    console.log("⏸️ 已暂停自动点击");
    setTimeout(autoClick, interval);
    return; // 暂停时不执行点击
  }

  // 尝试找到 Yes 按钮
  const yesBtn = document.querySelector('button.bg-green-500.rounded-full');
  // 尝试找到 Keep playing 按钮
  const keepBtn = document.querySelector('button.bg-primary.text-primary-foreground');

  if (yesBtn) {
    yesBtn.click();
    console.log("✅ 点击 Yes");
  } else if (keepBtn) {
    keepBtn.click();
    console.log("🎯 点击 Keep playing");
  } else {
    console.log("⏳ 未发现可点击按钮");
  }

  // 每隔 1 秒继续检测
  setTimeout(autoClick, interval);
}

// 启动脚本
autoClick();
