# FLOW-app
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="theme-color" content="#f7f4ff">
<title>FLOW</title>

<style>
:root{
  --bg:#f7f4ff;
  --card:#ffffff;
  --text:#29243a;
  --sub:#817b90;
  --line:#e8e1f0;
  --main:#8067d9;
  --light:#eee9ff;
  --good:#65a77f;
  --danger:#d86f7b;
  --shadow:0 5px 20px rgba(50,35,80,.08);
}

*{box-sizing:border-box}

body{
  margin:0;
  background:var(--bg);
  color:var(--text);
  font-family:-apple-system,BlinkMacSystemFont,"Noto Sans JP",sans-serif;
}

button,input,select{
  font:inherit;
}

button{
  border:0;
  cursor:pointer;
}

.app{
  max-width:760px;
  margin:auto;
  padding:16px 14px 100px;
}

header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin:5px 2px 18px;
}

.logo{
  font-size:28px;
  font-weight:900;
  letter-spacing:.08em;
}

.clock{
  color:var(--sub);
  font-size:12px;
}

.page{
  display:none;
}

.page.active{
  display:block;
}

.card{
  background:var(--card);
  border:1px solid var(--line);
  border-radius:20px;
  padding:16px;
  margin:10px 0;
  box-shadow:var(--shadow);
}

h1{
  font-size:25px;
  margin:0 0 5px;
}

h2{
  font-size:18px;
  margin:0 0 12px;
}

h3{
  margin:0;
}

p{
  margin:0;
}

.muted{
  color:var(--sub);
  font-size:13px;
}

.big{
  font-size:34px;
  font-weight:900;
}

.row{
  display:flex;
  gap:8px;
  align-items:center;
  flex-wrap:wrap;
}

.between{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:10px;
}

.grow{
  flex:1;
}

.grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:10px;
}

.grid3{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:8px;
}

.primary{
  background:var(--main);
  color:white;
  border-radius:13px;
  padding:12px 15px;
  font-weight:800;
}

.secondary{
  background:var(--light);
  color:#654db8;
  border-radius:13px;
  padding:10px 13px;
  font-weight:700;
}

.ghost{
  background:#f5f3f8;
  color:var(--text);
  border-radius:11px;
  padding:8px 10px;
}

.danger{
  background:#fff0f2;
  color:#b64d5a;
  border-radius:11px;
  padding:8px 10px;
}

.small{
  padding:7px 9px;
  font-size:12px;
}

input,select{
  width:100%;
  padding:10px;
  border:1px solid var(--line);
  border-radius:11px;
  background:white;
  color:var(--text);
}

label{
  display:block;
  margin:9px 0 4px;
  color:var(--sub);
  font-size:12px;
}

.progress{
  height:10px;
  background:#eeeaf4;
  border-radius:99px;
  overflow:hidden;
}

.progress i{
  display:block;
  height:100%;
  width:0;
  background:linear-gradient(90deg,var(--main),#a994ee);
}

.stat{
  background:#faf8fd;
  border-radius:15px;
  padding:12px;
}

.stat b{
  display:block;
  font-size:21px;
  margin-top:4px;
}

.task{
  display:flex;
  gap:9px;
  align-items:center;
  padding:11px 0;
  border-bottom:1px solid var(--line);
}

.task:last-child{
  border-bottom:0;
}

.check{
  width:23px;
  height:23px;
  flex:none;
  border:2px solid #cec7db;
  border-radius:8px;
  background:white;
  color:white;
  font-weight:bold;
}

.check.on{
  background:var(--good);
  border-color:var(--good);
}

.task.done .taskname{
  text-decoration:line-through;
  color:#aaa;
}

.tag{
  display:inline-block;
  padding:4px 7px;
  border-radius:99px;
  background:#f1edf8;
  color:#70677e;
  font-size:10px;
}

.taskname{
  font-weight:750;
}

.taskmeta{
  color:var(--sub);
  font-size:11px;
  margin-top:2px;
}

.timer{
  text-align:center;
  font-size:54px;
  font-weight:900;
  letter-spacing:.04em;
  margin:8px 0;
}

.timerSub{
  text-align:center;
  color:var(--sub);
  font-size:12px;
}

.routine{
  border:1px solid var(--line);
  border-radius:17px;
  padding:14px;
  margin:10px 0;
  background:white;
}

.routineIcon{
  font-size:32px;
}

.step{
  display:flex;
  gap:9px;
  align-items:center;
  padding:10px 0;
  border-bottom:1px solid var(--line);
}

.step:last-child{
  border-bottom:0;
}

.stepNumber{
  width:29px;
  height:29px;
  border-radius:50%;
  background:var(--light);
  color:var(--main);
  display:grid;
  place-items:center;
  font-weight:800;
  flex:none;
}

.modal{
  position:fixed;
  z-index:100;
  inset:0;
  background:rgba(30,24,53,.6);
  display:none;
  align-items:flex-end;
  justify-content:center;
  padding:12px;
}

.modal.show{
  display:flex;
}

.sheet{
  width:min(760px,100%);
  max-height:92vh;
  overflow:auto;
  background:white;
  border-radius:25px;
  padding:18px;
}

.close{
  float:right;
  width:32px;
  height:32px;
  border-radius:50%;
  background:#f1eef5;
  font-size:20px;
}

.toast{
  position:fixed;
  z-index:200;
  left:50%;
  bottom:88px;
  transform:translateX(-50%);
  background:#2e2938;
  color:white;
  border-radius:14px;
  padding:11px 15px;
  font-size:13px;
  display:none;
  max-width:90%;
  text-align:center;
}

.toast.show{
  display:block;
}

.empty{
  text-align:center;
  color:var(--sub);
  padding:20px 10px;
}

nav{
  position:fixed;
  z-index:90;
  bottom:0;
  left:0;
  right:0;
  display:flex;
  justify-content:center;
  background:white;
  border-top:1px solid var(--line);
  padding:8px 5px calc(8px + env(safe-area-inset-bottom));
}

nav button{
  flex:1;
  max-width:110px;
  background:transparent;
  color:var(--sub);
  border-radius:12px;
  padding:7px 4px;
  font-size:11px;
}

nav button.active{
  color:var(--main);
  background:var(--light);
  font-weight:800;
}

.barChart{
  display:flex;
  align-items:flex-end;
  gap:8px;
  height:130px;
}

.barItem{
  flex:1;
  text-align:center;
  font-size:9px;
  color:var(--sub);
}

.bar{
  width:100%;
  min-height:4px;
  background:#b5a5e9;
  border-radius:8px 8px 2px 2px;
  margin-bottom:5px;
}

@media(min-width:600px){
  nav{
    position:static;
    border:0;
    background:transparent;
    margin:auto;
    max-width:760px;
  }
}
</style>
</head>

<body>

<div class="app">

<header>
  <div class="logo">FLOW</div>
  <div id="clock" class="clock"></div>
</header>


<!-- HOME -->
<section id="home" class="page active">

  <div class="card">
    <div class="between">
      <div>
        <div class="muted">今日のFLOW</div>
        <div id="todayDate" class="big"></div>
      </div>
      <button class="secondary" onclick="openCondition()">
        状態を変更
      </button>
    </div>

    <div style="margin-top:18px">
      <div class="between">
        <span class="muted">今日の達成</span>
        <b id="homeRate">0%</b>
      </div>
      <div class="progress">
        <i id="homeProgress"></i>
      </div>
    </div>
  </div>


  <div class="card">

    <h2>今やること</h2>

    <div id="homeCurrent"></div>

    <button
      class="primary"
      style="width:100%;margin-top:10px"
      onclick="flowChoose()">
      FLOWに任せる
    </button>

    <button
      class="secondary"
      style="width:100%;margin-top:8px"
      onclick="startFiveMinute()">
      5分だけやる
    </button>

  </div>


  <div class="grid">

    <div class="stat">
      <span class="muted">FLOW TIME</span>
      <b id="homeTime">0分</b>
    </div>

    <div class="stat">
      <span class="muted">残りタスク</span>
      <b id="homeRemain">0</b>
    </div>

  </div>


  <div class="card">

    <h2>次の予定</h2>

    <div id="homeNextSchedule"></div>

  </div>


  <div class="card">

    <h2>今日のコンディション</h2>

    <div id="conditionView"></div>

  </div>


  <div id="breakSuggestion"></div>

</section>



<!-- MINIMUM -->
<section id="minimum" class="page">

  <div class="between">

    <div>
      <h1>最低限モード</h1>
      <p class="muted">
        今日やることを自由に追加・変更。
      </p>
    </div>

    <button class="primary" onclick="openTask()">
      ＋追加
    </button>

  </div>


  <div class="card">

    <div class="between">
      <b id="taskCount">0件</b>

      <button
        class="ghost small"
        onclick="clearCompleted()">
        完了を整理
      </button>
    </div>

    <div id="taskList"></div>

  </div>


  <div id="taskTimer"></div>

</section>



<!-- ROUTINE -->
<section id="routine" class="page">

  <div class="between">

    <div>
      <h1>ルーティン</h1>

      <p class="muted">
        最大3つまで。名前も中身も自由。
      </p>
    </div>

    <button class="primary" onclick="openRoutine()">
      ＋作成
    </button>

  </div>

  <div id="routineList"></div>

  <div id="routineTimer"></div>

</section>



<!-- SCHEDULE -->
<section id="schedule" class="page">

  <div class="between">

    <div>
      <h1>今日の予定</h1>

      <p class="muted">
        次の予定までの余裕時間も表示。
      </p>
    </div>

    <button class="primary" onclick="openSchedule()">
      ＋追加
    </button>

  </div>

  <div class="card">
    <div id="scheduleList"></div>
  </div>

  <div class="card">

    <h2>余裕時間</h2>

    <div id="freeTime"></div>

  </div>

</section>



<!-- STATS -->
<section id="stats" class="page">

  <h1>記録</h1>

  <p class="muted">
    FLOWのタイマーを使った時間を記録するよ。
  </p>


  <div class="grid" style="margin-top:12px">

    <div class="stat">
      <span class="muted">今日</span>
      <b id="statToday">0分</b>
    </div>

    <div class="stat">
      <span class="muted">7日</span>
      <b id="stat7">0分</b>
    </div>

    <div class="stat">
      <span class="muted">30日</span>
      <b id="stat30">0分</b>
    </div>

    <div class="stat">
      <span class="muted">完了率</span>
      <b id="statRate">0%</b>
    </div>

  </div>


  <div class="card">

    <h2>最近7日のFLOW TIME</h2>

    <div id="weekChart" class="barChart"></div>

  </div>


  <div class="card">

    <h2>カテゴリ別</h2>

    <div id="categoryStats"></div>

  </div>

</section>



<!-- SETTINGS -->
<section id="settings" class="page">

  <h1>設定</h1>


  <div class="card">

    <h2>バックアップ</h2>

    <p class="muted">
      データはこのiPhoneのブラウザに保存されます。
    </p>

    <div class="grid" style="margin-top:12px">

      <button
        class="secondary"
        onclick="exportData()">
        データ保存
      </button>

      <button
        class="secondary"
        onclick="document.getElementById('importFile').click()">
        データ読込
      </button>

    </div>

    <input
      id="importFile"
      type="file"
      accept=".json"
      style="display:none"
      onchange="importData(this.files[0])">

  </div>


  <div class="card">

    <h2>通知</h2>

    <p class="muted">
      ブラウザを開いている間の予定通知を設定できます。
    </p>

    <button
      class="secondary"
      style="margin-top:10px"
      onclick="requestNotification()">
      通知を許可する
    </button>

  </div>


  <div class="card">

    <h2>データ初期化</h2>

    <p class="muted">
      FLOWのデータをすべて削除します。
    </p>

    <button
      class="danger"
      style="margin-top:10px"
      onclick="resetAll()">
      全部リセット
    </button>

  </div>

</section>

</div>



<!-- NAV -->
<nav>

  <button
    data-page="home"
    onclick="go('home')">
    ⌂<br>ホーム
  </button>

  <button
    data-page="minimum"
    onclick="go('minimum')">
    ✓<br>最低限
  </button>

  <button
    data-page="routine"
    onclick="go('routine')">
    ↻<br>ルーティン
  </button>

  <button
    data-page="schedule"
    onclick="go('schedule')">
    ◷<br>予定
  </button>

  <button
    data-page="stats"
    onclick="go('stats')">
    ▥<br>記録
  </button>

  <button
    data-page="settings"
    onclick="go('settings')">
    ⚙<br>設定
  </button>

</nav>



<!-- MODAL -->
<div id="modal" class="modal">

  <div class="sheet">

    <button
      class="close"
      onclick="closeModal()">
      ×
    </button>

    <div id="modalBody"></div>

  </div>

</div>


<div id="toast" class="toast"></div>



<script>

/* =========================
   FLOW DATA
========================= */

const STORAGE_KEY = "FLOW_APP_V2";

const categories = [
  "勉強",
  "運動",
  "ダンス",
  "美容",
  "生活",
  "休憩",
  "その他"
];

let data = loadData();

let timerInterval = null;
let routineInterval = null;



/* =========================
   BASIC
========================= */

function uid(){

  return Date.now().toString(36) +
         Math.random().toString(36).slice(2);

}


function today(){

  const d = new Date();

  return d.getFullYear() + "-" +
    String(d.getMonth()+1).padStart(2,"0") + "-" +
    String(d.getDate()).padStart(2,"0");

}


function minutesNow(){

  const d = new Date();

  return d.getHours()*60 + d.getMinutes();

}


function formatTime(seconds){

  seconds = Math.max(0,Math.floor(seconds));

  const m = Math.floor(seconds/60);
  const s = seconds%60;

  return String(m).padStart(2,"0") +
    ":" +
    String(s).padStart(2,"0");

}


function escapeHTML(value){

  return String(value ?? "")
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");

}


function saveData(){

  localStorage.setItem(
    STORAGE_KEY,
    JSON.stringify(data)
  );

}


function defaultData(){

  return {

    tasks:[],

    routines:[],

    schedules:[],

    condition:"😐 普通",

    records:{},

    activeTask:null,

    activeRoutine:null

  };

}


function loadData(){

  try{

    const saved =
      localStorage.getItem(STORAGE_KEY);

    if(saved){

      const parsed = JSON.parse(saved);

      return {
        ...defaultData(),
        ...parsed
      };

    }

  }catch(error){

    console.log(error);

  }

  return defaultData();

}



/* =========================
   NAVIGATION
========================= */

function go(page){

  document
    .querySelectorAll(".page")
    .forEach(el=>{
      el.classList.remove("active");
    });

  const target =
    document.getElementById(page);

  if(target){
    target.classList.add("active");
  }

  document
    .querySelectorAll("nav button")
    .forEach(btn=>{
      btn.classList.toggle(
        "active",
        btn.dataset.page === page
      );
    });

  render();

}


document
  .querySelector('nav button[data-page="home"]')
  .classList.add("active");



/* =========================
   MODAL / TOAST
========================= */

function openModal(html){

  document.getElementById("modalBody").innerHTML = html;

  document
    .getElementById("modal")
    .classList.add("show");

}


function closeModal(){

  document
    .getElementById("modal")
    .classList.remove("show");

}


function toast(message){

  const el =
    document.getElementById("toast");

  el.textContent = message;

  el.classList.add("show");

  clearTimeout(el._timer);

  el._timer =
    setTimeout(()=>{
      el.classList.remove("show");
    },2500);

}



/* =========================
   HOME
========================= */

function renderHome(){

  const d = new Date();

  document.getElementById("todayDate")
    .textContent =
      `${d.getMonth()+1}/${d.getDate()}`;

  const total =
    data.tasks.length;

  const done =
    data.tasks.filter(t=>t.done).length;

  const rate =
    total === 0
      ? 0
      : Math.round(done/total*100);

  document.getElementById("homeRate")
    .textContent = rate + "%";

  document.getElementById("homeProgress")
    .style.width = rate + "%";

  document.getElementById("homeRemain")
    .textContent =
      data.tasks.filter(t=>!t.done).length;

  document.getElementById("homeTime")
    .textContent =
      Math.floor(getTotalForDays(1)/60) + "分";


  const current =
    document.getElementById("homeCurrent");


  if(data.activeTask){

    const task =
      data.tasks.find(
        t=>t.id===data.activeTask.id
      );

    if(task){

      current.innerHTML = `
        <div class="card" style="margin:0">
          <b>${escapeHTML(task.name)}</b>
          <div class="taskmeta">
            ${escapeHTML(task.category)}
          </div>
          <button
            class="primary"
            style="margin-top:10px"
            onclick="go('minimum')">
            タイマーを見る
          </button>
        </div>
      `;

    }

  }else if(data.activeRoutine){

    const r =
      data.routines.find(
        x=>x.id===data.activeRoutine.routineId
      );

    if(r){

      current.innerHTML = `
        <div class="card" style="margin:0">
          <b>${escapeHTML(r.icon)} ${escapeHTML(r.name)}</b>
          <div class="taskmeta">
            ルーティン実行中
          </div>
          <button
            class="primary"
            style="margin-top:10px"
            onclick="go('routine')">
            ルーティンを見る
          </button>
        </div>
      `;

    }

  }else{

    const next =
      data.tasks.find(t=>!t.done&&!t.deferred);

    current.innerHTML =
      next
      ? `
        <div>
          <b>${escapeHTML(next.name)}</b>
          <div class="taskmeta">
            ${escapeHTML(next.category)}
            ・目安 ${next.estimate}分
          </div>
        </div>
      `
      : `
        <div class="empty">
          今やることはないよ。✨
        </div>
      `;

  }


  const nextSchedule =
    getNextSchedule();

  document.getElementById("homeNextSchedule")
    .innerHTML =
      nextSchedule
      ? `
        <b>${escapeHTML(nextSchedule.time)}
       　${escapeHTML(nextSchedule.name)}</b>
        <div class="muted">
          あと ${nextSchedule.diff}分
        </div>
      `
      : `
        <div class="empty">
          今日の次の予定はありません。
        </div>
      `;


  document.getElementById("conditionView")
    .innerHTML = `
      <div style="font-size:20px">
        ${escapeHTML(data.condition)}
      </div>
    `;


  renderBreakSuggestion();

}



function renderBreakSuggestion(){

  const total =
    getTotalForDays(1);

  const box =
    document.getElementById("breakSuggestion");

  if(total >= 90*60){

    box.innerHTML = `
      <div class="card">
        <h2>ちょっと休憩しよ☕</h2>
        <p class="muted">
          今日90分以上FLOWしてるよ。
          5分くらい休憩してから続けるのもおすすめ。
        </p>
        <button
          class="secondary"
          style="margin-top:10px"
          onclick="startBreak()">
          5分休憩
        </button>
      </div>
    `;

  }else{

    box.innerHTML = "";

  }

}



/* =========================
   CONDITION
========================= */

function openCondition(){

  const options = [
    "😊 元気",
    "😐 普通",
    "😴 眠い",
    "🫠 しんどい"
  ];

  openModal(`
    <h2>今日のコンディション</h2>

    ${options.map(x=>`
      <button
        class="secondary"
        style="width:100%;margin:6px 0"
        onclick="setCondition('${x}')">
        ${x}
      </button>
    `).join("")}
  `);

}


function setCondition(value){

  data.condition = value;

  saveData();

  closeModal();

  render();

  toast("コンディションを更新したよ");

}



/* =========================
   TASKS
========================= */

function openTask(id=null){

  const task =
    id
    ? data.tasks.find(t=>t.id===id)
    : {
        name:"",
        category:"勉強",
        estimate:30,
        deferred:false
      };


  openModal(`

    <h2>${id?"タスク編集":"タスク追加"}</h2>

    <label>タスク名</label>

    <input
      id="taskName"
      value="${escapeHTML(task.name)}"
      placeholder="例：英単語30分">

    <label>カテゴリ</label>

    <select id="taskCategory">
      ${categories.map(c=>`
        <option
          ${c===task.category?"selected":""}>
          ${c}
        </option>
      `).join("")}
    </select>

    <label>目安時間（分）</label>

    <input
      id="taskEstimate"
      type="number"
      min="1"
      value="${task.estimate}">

    <div class="grid" style="margin-top:15px">

      <button
        class="primary"
        onclick="saveTask('${id||""}')">
        保存
      </button>

      ${
        id
        ? `
          <button
            class="danger"
            onclick="deleteTask('${id}')">
            削除
          </button>
        `
        : ""
      }

    </div>

  `);

}


function saveTask(id){

  const name =
    document.getElementById("taskName")
      .value.trim();

  if(!name){

    toast("タスク名を入れてね");

    return;

  }


  const category =
    document.getElementById("taskCategory")
      .value;

  const estimate =
    Math.max(
      1,
      Number(
        document.getElementById("taskEstimate").value
      ) || 30
    );


  if(id){

    const task =
      data.tasks.find(t=>t.id===id);

    if(task){

      task.name=name;
      task.category=category;
      task.estimate=estimate;

    }

  }else{

    data.tasks.push({

      id:uid(),

      name,

      category,

      estimate,

      done:false,

      deferred:false

    });

  }


  saveData();

  closeModal();

  render();

  toast("保存したよ");

}


function deleteTask(id){

  if(!confirm("このタスクを削除する？")) return;

  data.tasks =
    data.tasks.filter(t=>t.id!==id);

  if(data.activeTask?.id===id){

    data.activeTask=null;

  }

  saveData();

  closeModal();

  render();

}


function toggleTask(id){

  const task =
    data.tasks.find(t=>t.id===id);

  if(!task) return;

  task.done=!task.done;

  if(task.done){

    task.deferred=false;

  }

  saveData();

  render();

}


function deferTask(id){

  const task =
    data.tasks.find(t=>t.id===id);

  if(!task) return;

  task.deferred=!task.deferred;

  saveData();

  render();

  toast(
    task.deferred
      ? "あとでに移動したよ"
      : "タスクを戻したよ"
  );

}


function moveTask(id,direction){

  const index =
    data.tasks.findIndex(t=>t.id===id);

  if(index<0) return;

  const newIndex =
    index + direction;

  if(newIndex<0 ||
     newIndex>=data.tasks.length) return;

  [
    data.tasks[index],
    data.tasks[newIndex]
  ]=[
    data.tasks[newIndex],
    data.tasks[index]
  ];

  saveData();

  render();

}


function clearCompleted(){

  data.tasks =
    data.tasks.filter(t=>!t.done);

  saveData();

  render();

  toast("完了タスクを整理したよ");

}



/* =========================
   TASK RENDER
========================= */

function renderTasks(){

  document.getElementById("taskCount")
    .textContent =
      data.tasks.length + "件";


  const box =
    document.getElementById("taskList");


  if(!data.tasks.length){

    box.innerHTML = `
      <div class="empty">
        まだタスクがないよ。<br>
        「＋追加」から作ってみよう。
      </div>
    `;

  }else{

    box.innerHTML =
      data.tasks.map((task,index)=>`

        <div class="task
          ${task.done?"done":""}">

          <button
            class="check ${task.done?"on":""}"
            onclick="toggleTask('${task.id}')">
            ${task.done?"✓":""}
          </button>

          <div class="grow">

            <div class="taskname">
              ${escapeHTML(task.name)}
            </div>

            <div class="taskmeta">

              <span class="tag">
                ${escapeHTML(task.category)}
              </span>

              ${task.estimate}分

              ${
                task.deferred
                ? "・あとで"
                : ""
              }

            </div>

          </div>

          <button
            class="ghost small"
            onclick="startTask('${task.id}')">
            ▶
          </button>

          <button
            class="ghost small"
            onclick="openTask('${task.id}')">
            編集
          </button>

        </div>

        <div class="row"
             style="justify-content:flex-end;margin-top:-5px;margin-bottom:4px">

          <button
            class="ghost small"
            onclick="moveTask('${task.id}',-1)">
            ↑
          </button>

          <button
            class="ghost small"
            onclick="moveTask('${task.id}',1)">
            ↓
          </button>

          <button
            class="ghost small"
            onclick="deferTask('${task.id}')">
            ${task.deferred?"戻す":"あとで"}
          </button>

        </div>

      `).join("");

  }


  renderTaskTimer();

}



/* =========================
   TASK TIMER
========================= */

function startTask(id){

  if(data.activeTask){

    if(data.activeTask.id===id){

      return;

    }

    if(!confirm("今のタイマーを終了して別のタスクを始める？")){

      return;

    }

    stopTask(true);

  }


  data.activeTask={

    id,

    startedAt:Date.now(),

    elapsed:0,

    paused:false,

    pauseStarted:null

  };

  saveData();

  startTimerLoop();

  render();

  toast("タイマー開始！");

}


function pauseTask(){

  const a=data.activeTask;

  if(!a) return;

  if(!a.paused){

    a.elapsed =
      getTaskElapsed();

    a.paused=true;

    a.pauseStarted=Date.now();

    saveData();

    stopTimerLoop();

    render();

    toast("一時停止");

  }else{

    a.startedAt =
      Date.now() -
      a.elapsed*1000;

    a.paused=false;

    a.pauseStarted=null;

    saveData();

    startTimerLoop();

    render();

    toast("再開！");

  }

}


function getTaskElapsed(){

  const a=data.activeTask;

  if(!a) return 0;

  if(a.paused){

    return a.elapsed;

  }

  return a.elapsed +
    Math.floor(
      (Date.now()-a.startedAt)/1000
    );

}


function stopTask(finished=false){

  const a=data.activeTask;

  if(!a) return;

  const elapsed =
    getTaskElapsed();

  const task =
    data.tasks.find(t=>t.id===a.id);

  if(task){

    logTime(
      elapsed,
      task.category,
      task.name
    );

    if(finished){

      task.done=true;

    }

  }

  data.activeTask=null;

  stopTimerLoop();

  saveData();

  render();

}


function finishTask(){

  if(!data.activeTask) return;

  stopTask(true);

  toast("おつかれさま！タスク完了✨");

}


function interruptTask(){

  if(!data.activeTask) return;

  stopTask(false);

  toast("ここまでを記録して中断したよ");

}


function renderTaskTimer(){

  const box =
    document.getElementById("taskTimer");

  const a=data.activeTask;

  if(!a){

    box.innerHTML="";

    return;

  }


  const task =
    data.tasks.find(t=>t.id===a.id);

  if(!task){

    data.activeTask=null;

    saveData();

    box.innerHTML="";

    return;

  }


  box.innerHTML=`

    <div class="card">

      <h2>タイマー</h2>

      <div class="timer">
        ${formatTime(getTaskElapsed())}
      </div>

      <div class="timerSub">
        ${escapeHTML(task.name)}
      </div>

      <div class="row"
           style="justify-content:center;margin-top:12px">

        <button
          class="primary"
          onclick="pauseTask()">
          ${a.paused?"再開":"一時停止"}
        </button>

        <button
          class="secondary"
          onclick="finishTask()">
          完了
        </button>

        <button
          class="ghost"
          onclick="interruptTask()">
          中断
        </button>

      </div>

    </div>

  `;

}


function startTimerLoop(){

  stopTimerLoop();

  timerInterval =
    setInterval(()=>{

      renderTaskTimer();

      renderHome();

    },1000);

}


function stopTimerLoop(){

  if(timerInterval){

    clearInterval(timerInterval);

    timerInterval=null;

  }

}



/* =========================
   5 MIN MODE
========================= */

function startFiveMinute(){

  const available =
    data.tasks.find(
      t=>!t.done&&!t.deferred
    );

  if(!available){

    toast("まずタスクを1つ追加してね");

    return;

  }


  if(data.activeTask){

    toast("今のタイマーを先に終わらせてね");

    return;

  }


  data.activeTask={

    id:available.id,

    startedAt:Date.now(),

    elapsed:0,

    paused:false,

    fiveMinute:true

  };

  saveData();

  startTimerLoop();

  go("minimum");

  toast("5分だけスタート！");

}


function startBreak(){

  toast("5分休憩スタート☕");

  setTimeout(()=>{

    toast("休憩おわり！戻れそうなら再開しよう✨");

  },5*60*1000);

}



/* =========================
   ROUTINES
========================= */

function routineTotal(routine){

  return routine.steps
    .reduce(
      (sum,step)=>sum+Number(step.minutes),
      0
    );

}


function openRoutine(id=null){

  if(!id && data.routines.length>=3){

    toast("ルーティンは3つまでだよ");

    return;

  }


  const routine =
    id
    ? data.routines.find(r=>r.id===id)
    : {
        name:"新しいルーティン",
        icon:"✨",
        steps:[]
      };


  const steps =
    routine.steps.map(
      (step,index)=>stepEditorHTML(step,index)
    ).join("");


  openModal(`

    <h2>
      ${id?"ルーティン編集":"新しいルーティン"}
    </h2>

    <label>アイコン</label>

    <input
      id="routineIcon"
      maxlength="3"
      value="${escapeHTML(routine.icon)}">

    <label>ルーティン名</label>

    <input
      id="routineName"
      value="${escapeHTML(routine.name)}"
      placeholder="例：朝の準備">

    <div class="between"
         style="margin-top:14px">

      <b>ステップ</b>

      <button
        class="secondary small"
        onclick="addRoutineStep()">
        ＋ステップ
      </button>

    </div>

    <div id="routineStepEditor">
      ${steps}
    </div>

    <div class="grid"
         style="margin-top:15px">

      <button
        class="primary"
        onclick="saveRoutine('${id||""}')">
        保存
      </button>

      ${
        id
        ? `
          <button
            class="danger"
            onclick="deleteRoutine('${id}')">
            削除
          </button>
        `
        : ""
      }

    </div>

  `);

}


function stepEditorHTML(step,index){

  return `

    <div class="step">

      <span class="stepNumber">
        ${index+1}
      </span>

      <div class="grow">

        <input
          class="routineStepName"
          value="${escapeHTML(step.name)}"
          placeholder="ステップ名">

        <div class="grid"
             style="margin-top:6px">

          <input
            class="routineStepMinutes"
            type="number"
            min="1"
            value="${step.minutes}">

          <select
            class="routineStepCategory">

            ${categories.map(c=>`
              <option
                ${c===step.category?"selected":""}>
                ${c}
              </option>
            `).join("")}

          </select>

        </div>

      </div>

      <button
        class="danger small"
        onclick="this.parentElement.remove()">
        ×
      </button>

    </div>

  `;

}


function addRoutineStep(){

  const box =
    document.getElementById(
      "routineStepEditor"
    );

  const index =
    box.children.length;

  box.insertAdjacentHTML(
    "beforeend",
    stepEditorHTML(
      {
        name:"",
        minutes:5,
        category:"その他"
      },
      index
    )
  );

}


function saveRoutine(id){

  const name =
    document.getElementById(
      "routineName"
    ).value.trim() ||
    "無題ルーティン";

  const icon =
    document.getElementById(
      "routineIcon"
    ).value.trim() ||
    "✨";


  const elements =
    [...document.querySelectorAll(
      "#routineStepEditor .step"
    )];


  if(!elements.length){

    toast("ステップを1つ以上作ってね");

    return;

  }


  const steps =
    elements.map((el,index)=>({

      id:uid(),

      name:
        el.querySelector(
          ".routineStepName"
        ).value.trim() ||
        `ステップ${index+1}`,

      minutes:
        Math.max(
          1,
          Number(
            el.querySelector(
              ".routineStepMinutes"
            ).value
          ) || 5
        ),

      category:
        el.querySelector(
          ".routineStepCategory"
        ).value

    }));


  if(id){

    const routine =
      data.routines.find(r=>r.id===id);

    if(routine){

      routine.name=name;
      routine.icon=icon;
      routine.steps=steps;

    }

  }else{

    data.routines.push({

      id:uid(),

      name,

      icon,

      steps

    });

  }


  saveData();

  closeModal();

  render();

  toast("ルーティンを保存したよ");

}


function duplicateRoutine(id){

  if(data.routines.length>=3){

    toast("ルーティンは3つまでだよ");

    return;

  }


  const original =
    data.routines.find(r=>r.id===id);

  if(!original) return;


  data.routines.push({

    id:uid(),

    name:original.name+" コピー",

    icon:original.icon,

    steps:original.steps.map(
      s=>({...s,id:uid()})
    )

  });


  saveData();

  render();

  toast("ルーティンを複製したよ");

}


function deleteRoutine(id){

  if(!confirm("このルーティンを削除する？")){

    return;

  }

  data.routines =
    data.routines.filter(r=>r.id!==id);

  if(
    data.activeRoutine &&
    data.activeRoutine.routineId===id
  ){

    data.activeRoutine=null;

  }

  closeModal();

  saveData();

  render();

}



/* =========================
   ROUTINE TIMER
========================= */

function startRoutine(id){

  if(data.activeTask){

    toast("先に今のタスクを終わらせてね");

    return;

  }


  const routine =
    data.routines.find(r=>r.id===id);

  if(!routine || !routine.steps.length){

    toast("ステップがないよ");

    return;

  }


  data.activeRoutine={

    routineId:id,

    index:0,

    startedAt:Date.now(),

    elapsed:0,

    paused:false

  };

  saveData();

  startRoutineLoop();

  render();

  toast("ルーティン開始！");

}


function routineElapsed(){

  const a=data.activeRoutine;

  if(!a) return 0;

  if(a.paused) return a.elapsed;

  return a.elapsed +
    Math.floor(
      (Date.now()-a.startedAt)/1000
    );

}


function currentRoutineStep(){

  const a=data.activeRoutine;

  if(!a) return null;

  const routine =
    data.routines.find(
      r=>r.id===a.routineId
    );

  if(!routine) return null;

  return routine.steps[a.index] || null;

}


function pauseRoutine(){

  const a=data.activeRoutine;

  if(!a) return;


  if(!a.paused){

    a.elapsed=routineElapsed();

    a.paused=true;

    saveData();

    stopRoutineLoop();

    render();

  }else{

    a.startedAt =
      Date.now() -
      a.elapsed*1000;

    a.paused=false;

    saveData();

    startRoutineLoop();

    render();

  }

}


function skipRoutine(){

  const a=data.activeRoutine;

  if(!a) return;


  const step =
    currentRoutineStep();

  if(step){

    const elapsed =
      Math.min(
        routineElapsed(),
        step.minutes*60
      );

    logTime(
      elapsed,
      step.category,
      step.name
    );

  }


  nextRoutineStep();

}


function nextRoutineStep(){

  const a=data.activeRoutine;

  if(!a) return;


  const routine =
    data.routines.find(
      r=>r.id===a.routineId
    );

  a.index++;

  a.elapsed=0;

  a.startedAt=Date.now();


  if(
    !routine ||
    a.index>=routine.steps.length
  ){

    data.activeRoutine=null;

    stopRoutineLoop();

    saveData();

    render();

    toast("ルーティン完了！✨");

    return;

  }


  saveData();

  render();

}


function finishRoutine(){

  const a=data.activeRoutine;

  if(!a) return;


  const step=currentRoutineStep();

  if(step){

    logTime(
      Math.min(
        routineElapsed(),
        step.minutes*60
      ),
      step.category,
      step.name
    );

  }


  data.activeRoutine=null;

  stopRoutineLoop();

  saveData();

  render();

  toast("ルーティンを終了したよ");

}


function startRoutineLoop(){

  stopRoutineLoop();

  routineInterval =
    setInterval(()=>{

      const step =
        currentRoutineStep();

      if(!step) return;


      if(
        !data.activeRoutine.paused &&
        routineElapsed() >=
          step.minutes*60
      ){

        nextRoutineStep();

      }

      renderRoutineTimer();

    },500);

}


function stopRoutineLoop(){

  if(routineInterval){

    clearInterval(routineInterval);

    routineInterval=null;

  }

}


function renderRoutineTimer(){

  const box =
    document.getElementById(
      "routineTimer"
    );

  const a=data.activeRoutine;

  if(!a){

    box.innerHTML="";

    return;

  }


  const routine =
    data.routines.find(
      r=>r.id===a.routineId
    );

  const step =
    currentRoutineStep();

  if(!routine || !step){

    data.activeRoutine=null;

    saveData();

    box.innerHTML="";

    return;

  }


  const remaining =
    Math.max(
      0,
      step.minutes*60-routineElapsed()
    );


  box.innerHTML=`

    <div class="card">

      <h2>
        ${escapeHTML(routine.icon)}
        ${escapeHTML(routine.name)}
      </h2>

      <div class="timer">
        ${formatTime(remaining)}
      </div>

      <div class="timerSub">

        ${a.index+1}
        /
        ${routine.steps.length}

        ・

        ${escapeHTML(step.name)}

      </div>

      <div class="row"
           style="justify-content:center;margin-top:12px">

        <button
          class="primary"
          onclick="pauseRoutine()">
          ${a.paused?"再開":"一時停止"}
        </button>

        <button
          class="secondary"
          onclick="skipRoutine()">
          スキップ
        </button>

        <button
          class="ghost"
          onclick="finishRoutine()">
          終了
        </button>

      </div>

    </div>

  `;

}


function renderRoutines(){

  const box =
    document.getElementById(
      "routineList"
    );


  if(!data.routines.length){

    box.innerHTML=`

      <div class="card empty">

        まだルーティンがないよ。<br>
        最大3つまで好きなものを作れるよ✨

      </div>

    `;

  }else{

    box.innerHTML =
      data.routines.map((r,index)=>`

        <div class="routine">

          <div class="between">

            <div class="row">

              <div class="routineIcon">
                ${escapeHTML(r.icon)}
              </div>

              <div>

                <div style="font-weight:900">
                  ${escapeHTML(r.name)}
                </div>

                <div class="muted">
                  約${routineTotal(r)}分
                  ・${r.steps.length}ステップ
                </div>

              </div>

            </div>

            <button
              class="primary small"
              onclick="startRoutine('${r.id}')">
              ▶ 開始
            </button>

          </div>


          <div style="margin-top:10px">

            ${r.steps.map((s,i)=>`

              <div class="task">

                <span class="stepNumber">
                  ${i+1}
                </span>

                <div class="grow">

                  <b>
                    ${escapeHTML(s.name)}
                  </b>

                  <div class="taskmeta">
                    ${s.minutes}分
                    ・${escapeHTML(s.category)}
                  </div>

                </div>

              </div>

            `).join("")}

          </div>


          <div class="row"
               style="justify-content:flex-end;margin-top:10px">

            <button
              class="ghost small"
              onclick="openRoutine('${r.id}')">
              編集
            </button>

            <button
              class="ghost small"
              onclick="duplicateRoutine('${r.id}')">
              複製
            </button>

          </div>

        </div>

      `).join("");

  }


  renderRoutineTimer();

}



/* =========================
   SCHEDULE
========================= */

function getNextSchedule(){

  const now=minutesNow();

  const list =
    data.schedules
      .filter(s=>!s.done)
      .map(s=>{

        const parts =
          s.time.split(":");

        const m =
          Number(parts[0])*60+
          Number(parts[1]);

        return {
          ...s,
          minutes:m,
          diff:m-now
        };

      })
      .filter(s=>s.diff>=0)
      .sort(
        (a,b)=>a.minutes-b.minutes
      );

  return list[0] || null;

}


function openSchedule(id=null){

  const schedule =
    id
    ? data.schedules.find(s=>s.id===id)
    : {
        time:"18:00",
        name:"",
        remind:true,
        done:false
      };


  openModal(`

    <h2>
      ${id?"予定編集":"予定追加"}
    </h2>

    <label>時間</label>

    <input
      id="scheduleTime"
      type="time"
      value="${schedule.time}">

    <label>予定名</label>

    <input
      id="scheduleName"
      value="${escapeHTML(schedule.name)}"
      placeholder="例：塾">

    <label style="margin-top:12px">

      <input
        id="scheduleRemind"
        type="checkbox"
        ${schedule.remind?"checked":""}
        style="width:auto">

      5分前にリマインド

    </label>


    <div class="grid"
         style="margin-top:15px">

      <button
        class="primary"
        onclick="saveSchedule('${id||""}')">
        保存
      </button>

      ${
        id
        ? `
          <button
            class="danger"
            onclick="deleteSchedule('${id}')">
            削除
          </button>
        `
        : ""
      }

    </div>

  `);

}


function saveSchedule(id){

  const time =
    document.getElementById(
      "scheduleTime"
    ).value;

  const name =
    document.getElementById(
      "scheduleName"
    ).value.trim() ||
    "予定";

  const remind =
    document.getElementById(
      "scheduleRemind"
    ).checked;


  if(!time){

    toast("時間を選んでね");

    return;

  }


  if(id){

    const schedule =
      data.schedules.find(s=>s.id===id);

    if(schedule){

      schedule.time=time;
      schedule.name=name;
      schedule.remind=remind;
      schedule.done=false;
      schedule.notified=false;

    }

  }else{

    data.schedules.push({

      id:uid(),

      time,

      name,

      remind,

      done:false,

      notified:false

    });

  }


  saveData();

  closeModal();

  render();

}


function toggleSchedule(id){

  const s =
    data.schedules.find(x=>x.id===id);

  if(!s) return;

  s.done=!s.done;

  saveData();

  render();

}


function deleteSchedule(id){

  data.schedules =
    data.schedules.filter(
      s=>s.id!==id
    );

  saveData();

  closeModal();

  render();

}


function renderSchedules(){

  const box =
    document.getElementById(
      "scheduleList"
    );


  const schedules =
    [...data.schedules]
      .sort(
        (a,b)=>
          a.time.localeCompare(b.time)
      );


  if(!schedules.length){

    box.innerHTML=`

      <div class="empty">
        今日の予定はまだないよ。
      </div>

    `;

  }else{

    box.innerHTML =
      schedules.map(s=>`

        <div class="task">

          <button
            class="check ${s.done?"on":""}"
            onclick="toggleSchedule('${s.id}')">
            ${s.done?"✓":""}
          </button>

          <div class="grow">

            <b>
              ${escapeHTML(s.time)}
             　${escapeHTML(s.name)}
            </b>

            <div class="taskmeta">

              ${
                s.remind
                ? "5分前リマインドあり"
                : "リマインドなし"
              }

            </div>

          </div>

          <button
            class="ghost small"
            onclick="openSchedule('${s.id}')">
            編集
          </button>

        </div>

      `).join("");

  }


  const next =
    getNextSchedule();


  document.getElementById(
    "freeTime"
  ).innerHTML =

    next

    ? `

      <div class="big">
        ${next.diff}分
      </div>

      <div class="muted">
        「${escapeHTML(next.name)}」まで。
      </div>

    `

    : `

      <div>
        <b>時間に余裕あり✨</b>
      </div>

      <div class="muted">
        今日の次の予定はありません。
      </div>

    `;

}



/* =========================
   FLOW CHOOSE
========================= */

function flowChoose(){

  const free =
    getNextSchedule()
      ? getNextSchedule().diff
      : 9999;


  const condition =
    data.condition;


  let tasks =
    data.tasks.filter(
      t=>!t.done&&!t.deferred
    );


  if(!tasks.length &&
     !data.routines.length){

    toast("まずタスクかルーティンを追加してね");

    return;

  }


  let choice=null;


  if(
    condition.includes("しんどい") ||
    condition.includes("眠い")
  ){

    choice =
      tasks.sort(
        (a,b)=>a.estimate-b.estimate
      )[0];

  }else{

    choice =
      tasks.find(
        t=>t.estimate<=free
      ) ||
      tasks[0];

  }


  const suitableRoutines =
    data.routines.filter(
      r=>routineTotal(r)<=free
    );


  if(
    suitableRoutines.length &&
    (
      !choice ||
      (
        condition.includes("元気") &&
        free>=30
      )
    )
  ){

    suitableRoutines.sort(
      (a,b)=>
        routineTotal(a)-routineTotal(b)
    );

    const routine =
      condition.includes("元気") &&
      free>=30
      ? suitableRoutines[
          suitableRoutines.length-1
        ]
      : suitableRoutines[0];


    if(confirm(
      `${routine.icon} ${routine.name}\n約${routineTotal(routine)}分\n\nこれを始める？`
    )){

      startRoutine(routine.id);

    }

    return;

  }


  if(choice){

    if(confirm(
      `${choice.name}\n目安 ${choice.estimate}分\n\nこれを始める？`
    )){

      startTask(choice.id);

    }

    return;

  }


  toast("今できるものが見つからなかったよ");

}



/* =========================
   RECORDS
========================= */

function logTime(seconds,category,name){

  if(seconds<=0) return;


  const key=today();


  if(!data.records[key]){

    data.records[key]={

      total:0,

      categories:{}

    };

  }


  data.records[key].total += seconds;


  if(!data.records[key].categories[category]){

    data.records[key].categories[category]=0;

  }


  data.records[key].categories[category] +=
    seconds;


  saveData();

}


function getTotalForDays(days){

  let total=0;

  for(let i=0;i<days;i++){

    const d=new Date();

    d.setDate(
      d.getDate()-i
    );

    const key =
      d.getFullYear()+"-"+
      String(d.getMonth()+1).padStart(2,"0")+"-"+
      String(d.getDate()).padStart(2,"0");

    total +=
      data.records[key]?.total || 0;

  }

  return total;

}



/* =========================
   STATS
========================= */

function renderStats(){

  document.getElementById("statToday")
    .textContent =
      Math.floor(
        getTotalForDays(1)/60
      )+"分";

  document.getElementById("stat7")
    .textContent =
      Math.floor(
        getTotalForDays(7)/60
      )+"分";

  document.getElementById("stat30")
    .textContent =
      Math.floor(
        getTotalForDays(30)/60
      )+"分";


  const total =
    data.tasks.length;

  const done =
    data.tasks.filter(t=>t.done).length;

  document.getElementById("statRate")
    .textContent =
      (
        total
        ? Math.round(done/total*100)
        : 0
      )+"%";


  renderWeekChart();

  renderCategoryStats();

}


function renderWeekChart(){

  const box =
    document.getElementById(
      "weekChart"
    );


  const values=[];

  let max=1;


  for(let i=6;i>=0;i--){

    const d=new Date();

    d.setDate(
      d.getDate()-i
    );

    const key =
      d.getFullYear()+"-"+
      String(d.getMonth()+1).padStart(2,"0")+"-"+
      String(d.getDate()).padStart(2,"0");


    const value =
      data.records[key]?.total || 0;

    max=Math.max(max,value);

    values.push({
      day:d.toLocaleDateString(
        "ja-JP",
        {weekday:"short"}
      ),
      value
    });

  }


  box.innerHTML =
    values.map(x=>`

      <div class="barItem">

        <div
          class="bar"
          style="height:${Math.max(
            4,
            x.value/max*90
          )}px">
        </div>

        ${x.day}<br>
        ${Math.floor(x.value/60)}分

      </div>

    `).join("");

}


function renderCategoryStats(){

  const box =
    document.getElementById(
      "categoryStats"
    );


  const totals={};


  Object.values(data.records)
    .forEach(record=>{

      Object.entries(
        record.categories || {}
      ).forEach(([cat,time])=>{

        totals[cat] =
          (totals[cat]||0)+time;

      });

    });


  const list =
    Object.entries(totals)
      .sort(
        (a,b)=>b[1]-a[1]
      );


  box.innerHTML =
    list.length

    ? list.map(([cat,time])=>`

        <div
          class="between"
          style="
            padding:9px 0;
            border-bottom:1px solid var(--line)
          ">

          <span>
            ${escapeHTML(cat)}
          </span>

          <b>
            ${Math.floor(time/60)}分
          </b>

        </div>

      `).join("")

    : `

      <div class="empty">
        まだ記録がないよ。
      </div>

    `;

}



/* =========================
   BACKUP
========================= */

function exportData(){

  const blob =
    new Blob(
      [
        JSON.stringify(
          data,
          null,
          2
        )
      ],
      {
        type:"application/json"
      }
    );


  const url =
    URL.createObjectURL(blob);


  const a =
    document.createElement("a");

  a.href=url;

  a.download =
    "FLOW-backup-"+today()+".json";

  document.body.appendChild(a);

  a.click();

  a.remove();

  setTimeout(()=>{
    URL.revokeObjectURL(url);
  },1000);


  toast("バックアップを作ったよ");

}


function importData(file){

  if(!file) return;


  const reader =
    new FileReader();


  reader.onload=function(){

    try{

      const imported =
        JSON.parse(
          reader.result
        );


      if(
        !Array.isArray(imported.tasks) ||
        !Array.isArray(imported.routines)
      ){

        throw new Error();

      }


      data={
        ...defaultData(),
        ...imported
      };


      saveData();

      render();

      toast("バックアップを読み込んだよ");

    }catch(error){

      alert(
        "このバックアップは読み込めませんでした。"
      );

    }

  };


  reader.readAsText(file);

}


function resetAll(){

  if(
    !confirm(
      "FLOWのデータを全部削除する？"
    )
  ){

    return;

  }


  localStorage.removeItem(
    STORAGE_KEY
  );


  data=defaultData();

  saveData();

  render();

  toast("初期化したよ");

}



/* =========================
   NOTIFICATION
========================= */

async function requestNotification(){

  if(!("Notification" in window)){

    toast(
      "このブラウザでは通知に対応していないよ"
    );

    return;

  }


  const permission =
    await Notification.requestPermission();


  if(permission==="granted"){

    toast("通知を許可したよ");

  }else{

    toast("通知は許可されなかったよ");

  }

}


function checkNotifications(){

  if(
    !("Notification" in window) ||
    Notification.permission!=="granted"
  ){

    return;

  }


  const now=minutesNow();


  data.schedules.forEach(schedule=>{

    if(
      !schedule.remind ||
      schedule.done ||
      schedule.notified
    ){

      return;

    }


    const parts =
      schedule.time.split(":");


    const scheduleMinutes =
      Number(parts[0])*60+
      Number(parts[1]);


    if(
      scheduleMinutes-now===5
    ){

      new Notification(
        "FLOW：5分前",
        {
          body:schedule.name
        }
      );


      schedule.notified=true;

      saveData();

    }

  });

}



/* =========================
   RENDER
========================= */

function render(){

  renderHome();

  renderTasks();

  renderRoutines();

  renderSchedules();

  renderStats();

}


function updateClock(){

  const now=new Date();

  document.getElementById("clock")
    .textContent =
      now.toLocaleString(
        "ja-JP",
        {
          month:"numeric",
          day:"numeric",
          weekday:"short",
          hour:"2-digit",
          minute:"2-digit"
        }
      );

}


setInterval(
  updateClock,
  1000
);


setInterval(
  checkNotifications,
  30000
);


setInterval(
  ()=>{
    renderHome();
  },
  1000
);


/* =========================
   START
========================= */

updateClock();

render();

</script>

</body>
</html>