
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#f5f0e8">
<title>FLOW ♡</title>
<style>
:root {
  --bg:#f7f3ed;
  --paper:#fffdf9;
  --ink:#403b38;
  --muted:#8c827a;
  --accent:#b8a5c9;
  --soft:#eee6f4;
  --line:#e9e1d8;
  --good:#849d85;
  --danger:#bc7777;
}
*{box-sizing:border-box}
body{
  margin:0;background:var(--bg);color:var(--ink);
  font-family:-apple-system,BlinkMacSystemFont,"Hiragino Sans","Yu Gothic",sans-serif;
  font-size:15px;line-height:1.65
}
button,input,textarea,select{font:inherit}
button{cursor:pointer}
.app{max-width:720px;margin:auto;padding:18px 15px 105px}
header{padding:12px 3px 18px}
.eyebrow{font-size:11px;letter-spacing:2px;color:var(--muted)}
h1{font-size:29px;margin:2px 0;font-weight:750}
h2{font-size:17px;margin:0 0 12px}
h3{font-size:14px;margin:0 0 7px}
p{margin:7px 0}
.small{font-size:12px;color:var(--muted)}
.muted{color:var(--muted)}
.page{display:none}
.page.active{display:block}
.card{
  background:var(--paper);border:1px solid var(--line);
  border-radius:18px;padding:17px;margin:13px 0;
  box-shadow:0 4px 18px #40352b08
}
.row{display:flex;align-items:center;gap:9px}
.between{display:flex;align-items:center;justify-content:space-between;gap:10px}
.wrap{flex-wrap:wrap}
.grow{flex:1;min-width:0}
.btn{
  border:1px solid var(--line);border-radius:12px;
  padding:9px 12px;background:white;color:var(--ink)
}
.btn.primary{background:var(--soft);border-color:var(--soft)}
.btn.dark{background:var(--ink);color:white}
.btn.small{font-size:12px;padding:6px 9px}
.btn.danger{color:var(--danger)}
.btn:disabled{opacity:.4;cursor:not-allowed}
input,textarea,select{
  width:100%;border:1px solid var(--line);border-radius:10px;
  padding:10px;background:white;color:var(--ink);margin:4px 0 10px
}
textarea{min-height:78px;resize:vertical}
label{display:block;font-size:12px;color:var(--muted)}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.stat{background:var(--soft);border-radius:14px;padding:12px}
.big{font-size:28px;font-weight:750}
.progress{height:7px;border-radius:10px;background:#eee8e1;overflow:hidden;margin:10px 0}
.progress span{display:block;height:100%;background:var(--accent);border-radius:10px}
.pill{display:inline-block;background:#f2ede6;border-radius:20px;padding:3px 8px;font-size:11px;color:var(--muted)}
.pill.must{background:#f6e8e5;color:#a35e54}
.pill.prefer{background:#eee9f5;color:#75658c}
.pill.optional{background:#edf0e9;color:#64785f}
.task{display:flex;gap:10px;align-items:flex-start;border-bottom:1px solid var(--line);padding:11px 0}
.task:last-child{border-bottom:0}
.task input[type=checkbox]{width:21px;height:21px;margin:4px 0 0;accent-color:var(--accent);flex-shrink:0}
.task.done .task-name{text-decoration:line-through;color:var(--muted)}
.empty{text-align:center;padding:17px;color:var(--muted);font-size:13px}
.nav{
  position:fixed;z-index:5;bottom:0;left:0;right:0;
  display:flex;justify-content:center;gap:3px;
  background:#fffdf9f5;border-top:1px solid var(--line);
  padding:7px 3px max(8px,env(safe-area-inset-bottom));
  backdrop-filter:blur(12px)
}
.nav button{
  flex:1;max-width:105px;min-width:0;border:0;background:transparent;
  color:var(--muted);border-radius:11px;padding:7px 1px;font-size:11px
}
.nav button span{display:block;font-size:19px;line-height:1.3}
.nav button.active{background:var(--soft);color:var(--ink)}
.timer{text-align:center;padding:16px 0;font-size:43px;font-weight:750;font-variant-numeric:tabular-nums}
.step{padding:10px 0;border-bottom:1px solid var(--line)}
.history-entry{background:#faf7f2;border-radius:12px;padding:12px;margin-top:10px}
hr{border:0;border-top:1px solid var(--line);margin:15px 0}
.hidden{display:none!important}
.toast{
  position:fixed;z-index:20;bottom:95px;left:50%;
  transform:translateX(-50%);background:var(--ink);color:white;
  padding:9px 15px;border-radius:20px;font-size:13px;
  display:none;max-width:90%
}
.guide details{border-bottom:1px solid var(--line);padding:10px 0}
.guide summary{font-weight:700;cursor:pointer;padding:3px 0}
.guide ul{padding-left:22px}
.guide li{margin:5px 0}
.guide-note{background:#faf7f2;border-radius:12px;padding:12px;margin-top:12px}
.step-editor{
  display:grid;
  grid-template-columns:minmax(0,1fr) 78px minmax(110px,1fr);
  gap:6px;align-items:end;margin:9px 0
}
.step-editor input,.step-editor select{min-width:0;padding:9px 6px;font-size:12px}
.step-editor .remove{grid-column:1/-1;justify-self:end}
.prep-item{padding:12px 0;border-bottom:1px solid var(--line)}
.prep-item:last-child{border-bottom:0}
.prep-item label{display:flex;align-items:flex-start;gap:8px;color:var(--ink);font-size:14px}
.prep-item input{width:19px;height:19px;margin:3px 0;accent-color:var(--accent)}
@media(max-width:390px){
 .nav{gap:0}
 .nav button{font-size:10px}
 .nav button span{font-size:17px}
 .btn{padding:8px 10px}
 .step-editor{grid-template-columns:minmax(0,1fr) 65px 105px;gap:4px}
}
@media(min-width:600px){.app{padding-top:28px}}
</style>
</head>
<body>
<div class="app">
<header>
  <div class="eyebrow">MY LITTLE DAILY NOTE</div>
  <h1>FLOW ♡</h1>
  <div class="small" id="todayLabel"></div>
</header>

<section class="page active" id="page-home">
  <div class="card">
    <div class="between">
      <div><div class="small">今日の達成率</div><div class="big" id="homePercent">0%</div></div>
      <div style="text-align:right"><div class="small">今日のタスク</div><strong id="homeCount">0 / 0</strong></div>
    </div>
    <div class="progress"><span id="homeProgress" style="width:0%"></span></div>
    <div class="small" id="homeMessage">小さな一歩から始めよう。</div>
  </div>
  <div class="grid2">
    <div class="stat"><div class="small">残りのタスク</div><div class="big" id="remaining">0</div><div class="small">今日の分</div></div>
    <div class="stat"><div class="small">今日の記録時間</div><div class="big" id="todayTime">0分</div><div class="small">積み重ね中 ♡</div></div>
  </div>
  <div class="card">
    <div class="between"><h2>今日のタスク</h2><button class="btn small" onclick="showPage('tasks')">すべて見る →</button></div>
    <div id="homeTasks"></div>
  </div>
  <div class="card">
    <h2>わたしの目標</h2>
    <div id="homeGoals"></div>
    <button class="btn primary" onclick="showPage('goals')">目標を確認する</button>
  </div>
  <div class="card">
    <h2>今日の振り返り</h2>
    <p class="small">今日の自分に、少しだけ目を向けてみよう。</p>
    <button class="btn primary" onclick="showPage('review')">振り返りを書く ♡</button>
  </div>
</section>

<section class="page" id="page-tasks">
  <div class="card">
    <div class="between"><h2>今日のタスク</h2><span class="pill" id="taskCounter">0件</span></div>
    <p class="small">チェックは日付ごとに保存されます。</p>
    <div id="taskList"></div>
  </div>
  <div class="card">
    <h2>タスクを追加</h2>
    <label for="taskName">やること</label>
    <input id="taskName" placeholder="例：英単語を覚える">
    <div class="grid2">
      <div><label for="taskMins">予定時間（分）</label><input id="taskMins" type="number" min="1" value="15"></div>
      <div><label for="taskCat">カテゴリー</label><select id="taskCat"><option>勉強</option><option>学校</option><option>生活</option><option>運動</option><option>美容</option><option>その他</option></select></div>
    </div>
    <label for="taskGoal">関連する目標</label>
    <select id="taskGoal"></select>
    <button class="btn primary" onclick="addTask()">＋ タスクを追加</button>
  </div>
  <div class="card" id="activeTimerCard" class="hidden">
    <h2>タスク計測中</h2>
    <div id="activeTimerName"></div>
    <div class="timer" id="activeTimerClock">00:00</div>
    <button class="btn primary" onclick="stopTaskTimer(true)">計測終了・記録</button>
  </div>
</section>

<section class="page" id="page-goals">
  <div class="card"><h2>わたしの目標</h2><p class="small">目標を毎日の行動につなげよう。</p><div id="goalList"></div></div>
  <div class="card">
    <h2>新しい目標</h2>
    <label for="goalName">目標</label><input id="goalName" placeholder="例：看護学校に合格する">
    <label for="goalWhy">達成したい理由（任意）</label><textarea id="goalWhy" placeholder="どんな自分になりたい？"></textarea>
    <button class="btn primary" onclick="addGoal()">＋ 目標を追加</button>
  </div>
</section>

<section class="page" id="page-routines">
  <div class="card">
    <h2>わたしのルーティン</h2>
    <p class="small">各ステップの時間を自分で設定できます。最大3つです。</p>
    <div id="routineList"></div>
  </div>

  <div class="card">
    <h2 id="routineFormTitle">ルーティンを作る</h2>
    <label for="routineName">ルーティン名</label>
    <input id="routineName" placeholder="例：学校に行く準備">
    <div class="between">
      <h3>ステップ</h3>
      <button class="btn small" onclick="addRoutineStepRow()">＋ ステップ追加</button>
    </div>
    <div class="small">時間は自分で入力してください。自動で時間を割り当てることはありません。</div>
    <div id="routineStepEditor"></div>
    <hr>
    <div class="between"><span class="small">合計所要時間</span><strong id="routineTotal">0分</strong></div>
    <div class="row wrap" style="margin-top:12px">
      <button class="btn primary" onclick="saveRoutine()">保存する</button>
      <button class="btn" onclick="cancelRoutineEdit()">キャンセル</button>
    </div>
  </div>

  <div class="card hidden" id="routineRunner">
    <div class="between"><h2 id="runningTitle">ルーティン実行中</h2><span class="pill" id="routineStepCount"></span></div>
    <div class="timer" id="routineTimer">00:00</div>
    <div class="progress"><span id="routineProgress" style="width:0%"></span></div>
    <div id="runningSteps"></div>
    <div class="row wrap">
      <button class="btn" onclick="pauseRoutine()">一時停止 / 再開</button>
      <button class="btn danger" onclick="stopRoutine()">中断する</button>
    </div>
  </div>
</section>

<section class="page" id="page-prep">
  <div class="card">
    <h2>お出かけ準備タイマー</h2>
    <p class="small">出発時間に合わせて、今できる準備を整理します。</p>
    <label for="leaveTime">出発時刻</label>
    <input type="time" id="leaveTime" value="08:00">
    <label for="prepRoutineSelect">登録済みルーティン</label>
    <select id="prepRoutineSelect"><option value="">ルーティンを選んでください</option></select>
    <button class="btn" onclick="appendSelectedRoutineToPrep()">＋ ルーティンを追加</button>
    <hr>
    <h3>今回の準備項目</h3>
    <p class="small">追加した項目の時間や優先度は、この画面だけで調整できます。</p>
    <div id="prepItems"></div>
    <div class="row wrap">
      <button class="btn" onclick="addPrepItem()">＋ 項目を追加</button>
      <button class="btn primary" onclick="planPrep()">準備プランを作る</button>
    </div>
    <div class="stat" style="margin-top:14px">
      <div class="small">出発まで</div>
      <div class="big" id="prepRemaining">--分</div>
    </div>
  </div>

  <div class="card hidden" id="prepResult">
    <h2>今回の準備プラン</h2>
    <div class="notice" id="prepMessage"></div>
    <div id="prepPlan"></div>
    <hr>
    <div class="between"><span class="small">選択した準備の合計</span><strong id="prepTotal">0分</strong></div>
    <div class="small" id="prepDifference"></div>
    <button class="btn primary" style="margin-top:12px" onclick="acceptPrepPlan()">この提案で準備を開始</button>
  </div>

  <div class="card">
    <h2>準備タイマー</h2>
    <div class="small" id="prepTimerName">実行中の準備はありません。</div>
    <div class="timer" id="prepClock">00:00</div>
    <div class="row wrap">
      <button class="btn primary" onclick="startPrepClock()">開始 / 再開</button>
      <button class="btn" onclick="pausePrepClock()">一時停止</button>
      <button class="btn" onclick="nextPrepStep()">次の項目へ</button>
      <button class="btn danger" onclick="stopPrepClock()">終了</button>
    </div>
    <div id="prepCurrentStep" class="small" style="text-align:center;margin-top:10px"></div>
  </div>

  <div class="card">
    <h2>5分だけ集中</h2>
    <p class="small">まずは5分だけ始めてみましょう。</p>
    <div class="timer" id="focusClock">05:00</div>
    <button class="btn primary" onclick="startFocus()">スタート</button>
    <button class="btn" onclick="stopFocus()">停止・リセット</button>
  </div>
</section>

<section class="page" id="page-review">
  <div class="card">
    <h2>今日の振り返り</h2>
    <p class="small">できたことも、うまくいかなかったことも、次に活かすための記録です。</p>
    <label for="reflectionWin">今日できたこと・頑張ったこと</label>
    <textarea id="reflectionWin" placeholder="小さなことでも大丈夫です"></textarea>
    <label for="reflectionBlock">困ったこと・改善したいこと</label>
    <textarea id="reflectionBlock" placeholder="次に工夫できそうなことは？"></textarea>
    <label for="reflectionNext">明日やりたいこと</label>
    <textarea id="reflectionNext" placeholder="明日の自分へのメモ"></textarea>
    <button class="btn primary" onclick="saveReflection()">今日の振り返りを保存</button>
    <p class="small" id="reflectionSaved"></p>
  </div>
  <div class="card">
    <div class="between"><h2>過去の振り返り</h2><button class="btn small" id="historyToggle" onclick="toggleReflectionHistory()">履歴を見る</button></div>
    <p class="small">読み返したいときだけ開けます。</p>
    <div id="reflectionHistory" class="hidden"></div>
  </div>
  <div class="card">
    <h2>今日の記録</h2>
    <div class="grid2">
      <div class="stat"><div class="small">完了したタスク</div><div class="big" id="reviewDone">0</div></div>
      <div class="stat"><div class="small">集中した時間</div><div class="big" id="reviewTime">0分</div></div>
    </div>
  </div>
</section>

<section class="page" id="page-settings">
  <div class="card">
    <h2>FLOWの設定</h2>
    <label for="themeChoice">テーマ</label>
    <select id="themeChoice" onchange="changeTheme(this.value)">
      <option value="beige">ミルクベージュ</option>
      <option value="lavender">ラベンダー × 白</option>
      <option value="mono">モノトーン</option>
    </select>
  </div>
  <div class="card">
    <h2>使い方・ガイド</h2>
    <button class="btn primary" onclick="showPage('guide')">使い方・ガイドを読む →</button>
  </div>
  <div class="card">
    <h2>データのバックアップ</h2>
    <p class="small">タスク・目標・ルーティン・記録・振り返りをJSONファイルに保存します。</p>
    <button class="btn primary" onclick="exportData()">バックアップを書き出す</button>
    <hr>
    <label for="importFile">バックアップファイルから復元</label>
    <input type="file" id="importFile" accept=".json,application/json">
    <button class="btn" onclick="importData()">バックアップを復元</button>
  </div>
  <div class="card">
    <h2>保存について</h2>
    <p class="small">データはこのブラウザ内に保存されます。定期的にバックアップしてください。</p>
    <button class="btn danger" onclick="resetApp()">アプリのデータを初期化</button>
  </div>
</section>

<section class="page" id="page-guide">
  <div class="card">
    <div class="between"><h2>使い方・ガイド</h2><button class="btn small" onclick="showPage('settings')">← 戻る</button></div>
    <div class="guide">
      <details open><summary>1. FLOWでできること</summary><p>目標を日々のタスクにつなげ、ルーティンや準備時間を整理し、振り返りを残すアプリです。</p></details>
      <details><summary>2. タスク</summary><p>やること、目安時間、カテゴリー、関連する目標を設定できます。チェックは日付ごとに保存されます。</p></details>
      <details><summary>3. 目標</summary><p>目標と理由を登録し、達成したら達成済みにできます。</p></details>
      <details><summary>4. ルーティンの作成</summary>
        <ul>
          <li>最大3つまで登録できます。</li>
          <li>ステップ名、所要時間、優先度を1つずつ入力します。</li>
          <li>時間は自動で決められません。自分で入力した時間が保存されます。</li>
          <li>保存後も編集・追加・削除ができます。</li>
          <li>優先度は「必須」「できればやる」「省略可能」から選びます。</li>
        </ul>
      </details>
      <details><summary>5. PREP</summary>
        <ul>
          <li>出発時刻を設定し、ルーティンを追加します。</li>
          <li>今回の準備項目ごとに時間と優先度を確認できます。</li>
          <li>必須を優先し、残り時間に応じて他の項目を提案します。</li>
          <li>元のルーティンは変更されません。</li>
          <li>提案は一時的な準備プランです。項目の選択は自分で変更できます。</li>
        </ul>
      </details>
      <details><summary>6. 振り返り</summary><p>今日できたこと、改善したいこと、明日やりたいことを保存します。過去の記録は必要なときだけ開けます。</p></details>
      <details><summary>7. バックアップ</summary><p>設定からJSON形式で保存できます。復元すると現在のデータが選択したバックアップの内容に置き換わります。</p></details>
      <details><summary>8. 保存と注意点</summary><p>データはブラウザ内に保存されます。別端末とは自動同期されません。ブラウザのデータ削除などで失われる可能性があるため、定期的にバックアップしてください。</p></details>
    </div>
    <div class="guide-note"><strong>大切なお知らせ</strong><p>予定どおりに進まない日があっても大丈夫。必要に応じて調整し、自分のペースで使ってください。</p></div>
  </div>
</section>

</div>

<nav class="nav">
  <button class="active" data-page="home" onclick="showPage('home')"><span>⌂</span>ホーム</button>
  <button data-page="tasks" onclick="showPage('tasks')"><span>☑</span>タスク</button>
  <button data-page="goals" onclick="showPage('goals')"><span>☆</span>目標</button>
  <button data-page="routines" onclick="showPage('routines')"><span>↻</span>ルーティン</button>
  <button data-page="prep" onclick="showPage('prep')"><span>◷</span>準備</button>
  <button data-page="review" onclick="showPage('review')"><span>♡</span>振り返り</button>
  <button data-page="settings" onclick="showPage('settings')"><span>⚙</span>設定</button>
</nav>
<div class="toast" id="toast"></div>

<script>
"use strict";

const STORE="FLOW_APP_V2";
const LEGACY="FLOW_COMPLETE_V1";
const $=id=>document.getElementById(id);
const uid=()=>Date.now().toString(36)+Math.random().toString(36).slice(2,8);
const dateKey=(d=new Date())=>d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0");
const esc=s=>String(s??"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const priorityLabels={must:"必須",prefer:"できればやる",optional:"省略可能"};

function fresh(){
 return {
  version:3,theme:"beige",
  goals:[
   {id:uid(),name:"看護学校に合格する",why:"自分の目標に向かって進む",done:false},
   {id:uid(),name:"体力をつける",why:"毎日を元気に過ごす",done:false},
   {id:uid(),name:"毎日英単語を覚える",why:"少しずつ積み重ねる",done:false}
  ],
  tasks:[],routines:[],records:{},reflection:{},dailyTasks:{}
 };
}

function normalize(x){
 const f=fresh();
 x=x&&typeof x==="object"?x:{};

 const tasks=Array.isArray(x.tasks)?x.tasks.map((t,i)=>({
  ...t,id:t.id||uid(),name:t.name||"やること",
  cat:t.cat||"その他",
  mins:Math.max(1,Number(t.mins??t.estimate??15)||15),
  goalId:t.goalId||"",done:!!t.done,order:Number(t.order??i)
 })):[ ];

 const dailyTasks=x.dailyTasks&&typeof x.dailyTasks==="object"?x.dailyTasks:{};
 if(!x.dailyTasks){
  dailyTasks[dateKey()]={};
  tasks.forEach(t=>{if(t.done)dailyTasks[dateKey()][String(t.id)]=true});
 }

 const routines=(Array.isArray(x.routines)?x.routines:[]).slice(0,3).map(r=>({
  ...r,id:r.id||uid(),name:r.name||"ルーティン",
  steps:(Array.isArray(r.steps)?r.steps:[]).map(s=>{
   const old=typeof s==="string"?{name:s}:s;
   const mins=Number(old.mins??old.min);
   return {
    id:old.id||uid(),
    name:old.name||"ステップ",
    mins:Number.isFinite(mins)&&mins>0?mins:null,
    priority:["must","prefer","optional"].includes(old.priority)?old.priority:"prefer"
   };
  })
 }));

 const goals=Array.isArray(x.goals)?x.goals:f.goals;
 return {
  ...f,...x,
  version:3,
  tasks,
  goals:goals.map(g=>({...g,id:g.id||uid()})),
  routines,dailyTasks,
  records:x.records&&typeof x.records==="object"?x.records:{},
  reflection:x.reflection&&typeof x.reflection==="object"?x.reflection:{},
  theme:x.theme||"beige"
 };
}

function loadDB(){
 try{
  let raw=localStorage.getItem(STORE);
  if(!raw)raw=localStorage.getItem(LEGACY);
  if(raw)return normalize(JSON.parse(raw));
 }catch(e){console.warn("FLOW data could not be read",e)}
 return fresh();
}

let db=loadDB();

function save(){
 try{localStorage.setItem(STORE,JSON.stringify(db))}
 catch(e){toast("保存できませんでした。バックアップを確認してください。")}
}

function toast(msg){
 const el=$("toast");
 el.textContent=msg;
 el.style.display="block";
 clearTimeout(toast.timer);
 toast.timer=setTimeout(()=>el.style.display="none",2400);
}

function taskDone(id,k=dateKey()){
 return !!db.dailyTasks?.[k]?.[String(id)];
}
function setTaskDone(id,value,k=dateKey()){
 if(!db.dailyTasks)db.dailyTasks={};
 if(!db.dailyTasks[k])db.dailyTasks[k]={};
 db.dailyTasks[k][String(id)]=!!value;
 save();
}
function todayTasks(){return db.tasks.map(t=>({...t,done:taskDone(t.id)}))}
function todaySeconds(){
 return (db.records[dateKey()]||[]).reduce((a,r)=>a+Number(r.sec||0),0);
}
function fmtTime(sec){
 sec=Math.max(0,Math.floor(sec));
 return String(Math.floor(sec/60)).padStart(2,"0")+":"+String(sec%60).padStart(2,"0");
}
function minutesText(sec){
 const n=Math.round(sec/60);
 return n<60?n+"分":Math.floor(n/60)+"時間"+(n%60?n%60+"分":"");
}

function showPage(name){
 document.querySelectorAll(".page").forEach(p=>p.classList.toggle("active",p.id==="page-"+name));
 document.querySelectorAll(".nav button").forEach(b=>b.classList.toggle("active",b.dataset.page===name));
 if(name==="review")loadTodayReflection();
 render();
 window.scrollTo({top:0,behavior:"smooth"});
}

function applyTheme(){
 const themes={
  beige:["#f7f3ed","#fffdf9","#403b38","#8c827a","#b8a5c9","#eee6f4","#e9e1d8"],
  lavender:["#f5f1fa","#fffefe","#393440","#898092","#b8a2d5","#eee5f8","#e8dfef"],
  mono:["#f1f1f1","#ffffff","#292929","#777777","#777777","#e7e7e7","#dddddd"]
 };
 const t=themes[db.theme]||themes.beige;
 ["--bg","--paper","--ink","--muted","--accent","--soft","--line"].forEach((k,i)=>document.documentElement.style.setProperty(k,t[i]));
 if($("themeChoice"))$("themeChoice").value=db.theme;
}

function render(){
 applyTheme();
 $("todayLabel").textContent=new Date().toLocaleDateString("ja-JP",{year:"numeric",month:"long",day:"numeric",weekday:"long"});
 renderHome();renderTasks();renderGoals();renderRoutines();
 renderPrepRoutineOptions();renderReview();
}

function renderHome(){
 const ts=todayTasks(),done=ts.filter(t=>t.done).length,total=ts.length;
 const pct=total?Math.round(done/total*100):0;
 $("homePercent").textContent=pct+"%";
 $("homeCount").textContent=done+" / "+total;
 $("homeProgress").style.width=pct+"%";
 $("remaining").textContent=total-done;
 $("todayTime").textContent=minutesText(todaySeconds());
 $("homeMessage").textContent=total&&done===total?"今日もよく頑張りました！ ♡":done?"いい感じ！少しずつ進んでいます。":"小さな一歩から始めましょう。";
 $("homeTasks").innerHTML=ts.length?ts.slice(0,5).map(taskHTML).join(""):'<div class="empty">タスクを追加してみましょう ♡</div>';
 $("homeGoals").innerHTML=db.goals.length?db.goals.filter(g=>!g.done).slice(0,3).map(g=>`<div class="step">☆ ${esc(g.name)}</div>`).join(""):'<div class="empty">目標を追加してみましょう</div>';
}

function taskHTML(t){
 return `<div class="task ${t.done?"done":""}">
  <input type="checkbox" ${t.done?"checked":""} onchange="toggleTask('${esc(t.id)}',this.checked)">
  <div class="grow"><div class="task-name">${esc(t.name)}</div><div class="small">${esc(t.cat)} ・ ${Number(t.mins)||0}分</div></div>
  <button class="btn small" onclick="startTaskTimer('${esc(t.id)}')">計測</button>
  <button class="btn small danger" onclick="deleteTask('${esc(t.id)}')">削除</button>
 </div>`;
}

function renderTasks(){
 const ts=todayTasks().sort((a,b)=>a.order-b.order);
 $("taskCounter").textContent=ts.filter(t=>t.done).length+"/"+ts.length+"件";
 $("taskList").innerHTML=ts.length?ts.map(taskHTML).join(""):'<div class="empty">まだタスクがありません。下から追加してください。</div>';
 $("taskGoal").innerHTML='<option value="">目標と関連づけない</option>'+db.goals.map(g=>`<option value="${esc(g.id)}">${esc(g.name)}</option>`).join("");
}

function toggleTask(id,checked){
 setTaskDone(id,checked);render();
 toast(checked?"タスク完了！おつかれさま ♡":"チェックを戻しました");
}
function addTask(){
 const name=$("taskName").value.trim();
 if(!name)return toast("タスク名を入力してください");
 db.tasks.push({id:uid(),name,cat:$("taskCat").value,mins:Math.max(1,Number($("taskMins").value)||15),goalId:$("taskGoal").value,order:db.tasks.length});
 $("taskName").value="";save();render();toast("タスクを追加しました");
}
function deleteTask(id){
 if(!confirm("このタスクを削除しますか？"))return;
 db.tasks=db.tasks.filter(t=>String(t.id)!==String(id));
 save();render();
}

function addGoal(){
 const name=$("goalName").value.trim();
 if(!name)return toast("目標を入力してください");
 db.goals.push({id:uid(),name,why:$("goalWhy").value.trim(),done:false});
 $("goalName").value="";$("goalWhy").value="";
 save();render();toast("目標を追加しました");
}
function renderGoals(){
 $("goalList").innerHTML=db.goals.length?db.goals.map(g=>{
  const related=db.tasks.filter(t=>String(t.goalId)===String(g.id));
  return `<div class="step">
   <div class="between"><strong>${esc(g.name)}</strong><button class="btn small" onclick="toggleGoal('${esc(g.id)}')">${g.done?"達成済み ✓":"達成にする"}</button></div>
   ${g.why?`<div class="small">${esc(g.why)}</div>`:""}
   <div class="small">関連タスク：${related.length}件</div>
   ${related.map(t=>`<div class="small">・${esc(t.name)}${taskDone(t.id)?" ✓":""}</div>`).join("")}
   <button class="btn small danger" style="margin-top:7px" onclick="deleteGoal('${esc(g.id)}')">削除</button>
  </div>`;
 }).join(""):'<div class="empty">目標を追加してみましょう。</div>';
}
function toggleGoal(id){
 const g=db.goals.find(x=>String(x.id)===String(id));
 if(g)g.done=!g.done;save();render();
}
function deleteGoal(id){
 if(!confirm("この目標を削除しますか？"))return;
 db.goals=db.goals.filter(g=>String(g.id)!==String(id));save();render();
}

/* ROUTINE EDITOR */
let editingRoutineId=null;

function addRoutineStepRow(step={}){
 const editor=$("routineStepEditor");
 const row=document.createElement("div");
 row.className="step-editor";
 const name=document.createElement("input");
 name.className="routine-step-name";
 name.placeholder="ステップ名";
 name.value=step.name||"";
 const mins=document.createElement("input");
 mins.className="routine-step-mins";
 mins.type="number";mins.min="1";mins.step="1";
 mins.placeholder="分";
 mins.value=step.mins??"";
 const priority=document.createElement("select");
 priority.className="routine-step-priority";
 [["must","必須"],["prefer","できればやる"],["optional","省略可能"]].forEach(([v,l])=>{
  const o=document.createElement("option");o.value=v;o.textContent=l;
  priority.appendChild(o);
 });
 priority.value=step.priority||"prefer";
 const remove=document.createElement("button");
 remove.type="button";remove.className="btn small danger remove";
 remove.textContent="このステップを削除";
 remove.onclick=()=>{row.remove();updateRoutineTotal()};
 [name,mins,priority].forEach(el=>el.addEventListener("input",updateRoutineTotal));
 row.append(name,mins,priority,remove);
 editor.appendChild(row);
 updateRoutineTotal();
}

function readRoutineEditor(){
 return [...document.querySelectorAll("#routineStepEditor .step-editor")].map(row=>{
  const name=row.querySelector(".routine-step-name").value.trim();
  const raw=row.querySelector(".routine-step-mins").value;
  const mins=raw===""?null:Number(raw);
  return {
   id:row.dataset.id||uid(),name,mins,
   priority:row.querySelector(".routine-step-priority").value
  };
 }).filter(s=>s.name);
}

function updateRoutineTotal(){
 const rows=[...document.querySelectorAll("#routineStepEditor .step-editor")];
 let total=0,missing=0;
 rows.forEach(row=>{
  const v=row.querySelector(".routine-step-mins").value;
  if(v===""||!Number.isFinite(Number(v))||Number(v)<=0)missing++;
  else total+=Number(v);
 });
 $("routineTotal").textContent=total+"分"+(missing?"（時間未入力 "+missing+"件）":"");
}

function createRoutine(){
 if(db.routines.length>=3)return toast("ルーティンは最大3つまでです");
 editingRoutineId=null;
 $("routineFormTitle").textContent="ルーティンを作る";
 $("routineName").value="";
 $("routineStepEditor").innerHTML="";
 addRoutineStepRow();
 $("routineName").scrollIntoView({behavior:"smooth",block:"center"});
}

function editRoutine(id){
 const r=db.routines.find(x=>String(x.id)===String(id));
 if(!r)return;
 editingRoutineId=r.id;
 $("routineFormTitle").textContent="ルーティンを編集";
 $("routineName").value=r.name;
 $("routineStepEditor").innerHTML="";
 r.steps.forEach(s=>{
  const rowBefore=$("routineStepEditor").children.length;
  addRoutineStepRow(s);
  const row=$("routineStepEditor").children[rowBefore];
  row.dataset.id=s.id;
 });
 $("routineName").scrollIntoView({behavior:"smooth",block:"center"});
}

function cancelRoutineEdit(){
 editingRoutineId=null;
 $("routineName").value="";
 $("routineStepEditor").innerHTML="";
 $("routineFormTitle").textContent="ルーティンを作る";
 updateRoutineTotal();
}

function saveRoutine(){
 const name=$("routineName").value.trim();
 const steps=readRoutineEditor();
 if(!name)return toast("ルーティン名を入力してください");
 if(!steps.length)return toast("ステップを1つ以上追加してください");
 const invalid=steps.some(s=>!Number.isFinite(s.mins)||s.mins<=0);
 if(invalid)return toast("各ステップの時間を1分以上で入力してください");

 const clean=steps.map(s=>({...s,mins:Math.round(s.mins)}));
 if(editingRoutineId){
  const r=db.routines.find(x=>String(x.id)===String(editingRoutineId));
  if(!r)return toast("ルーティンが見つかりません");
  r.name=name;r.steps=clean;
  toast("ルーティンを更新しました");
 }else{
  if(db.routines.length>=3)return toast("ルーティンは最大3つまでです");
  db.routines.push({id:uid(),name,steps:clean});
  toast("ルーティンを保存しました");
 }
 cancelRoutineEdit();save();render();
}

function routineTotal(r){
 return r.steps.reduce((sum,s)=>sum+(Number(s.mins)||0),0);
}

function renderRoutines(){
 $("routineList").innerHTML=db.routines.length?db.routines.map(r=>`
  <div class="step">
   <div class="between">
    <strong>${esc(r.name)}</strong>
    <span class="pill">${routineTotal(r)}分</span>
   </div>
   ${r.steps.map((s,i)=>`
    <div class="step">
     <div class="between"><span>${i+1}. ${esc(s.name)}</span><strong>${s.mins??"未設定"}分</strong></div>
     <div class="row wrap">
      <span class="pill ${s.priority}">${priorityLabels[s.priority]||"できればやる"}</span>
     </div>
    </div>
   `).join("")}
   <div class="row wrap" style="margin-top:10px">
    <button class="btn primary small" onclick="startRoutine('${esc(r.id)}')">開始</button>
    <button class="btn small" onclick="editRoutine('${esc(r.id)}')">編集</button>
    <button class="btn small danger" onclick="deleteRoutine('${esc(r.id)}')">削除</button>
   </div>
  </div>
 `).join(""):'<div class="empty">ルーティンを作ってみましょう。</div>';
 if(routineState)renderRunningSteps();
}

function deleteRoutine(id){
 if(!confirm("このルーティンを削除しますか？"))return;
 if(routineState&&String(routineState.id)===String(id))stopRoutine();
 db.routines=db.routines.filter(r=>String(r.id)!==String(id));
 save();render();
}

/* ROUTINE TIMER */
let routineState=null,routineInterval=null;

function startRoutine(id){
 const r=db.routines.find(x=>String(x.id)===String(id));
 if(!r||!r.steps.length)return;
 if(r.steps.some(s=>!s.mins))return toast("時間が未入力のステップがあります。編集してください。");
 stopRoutine();
 routineState={id:r.id,index:0,started:Date.now(),stepStarted:Date.now(),elapsedBeforeStep:0,paused:false,pausedAt:0};
 $("routineRunner").classList.remove("hidden");
 $("runningTitle").textContent=r.name;
 showPage("routines");
 renderRunningSteps();startRoutineInterval();
}

function currentRoutine(){
 return routineState?db.routines.find(r=>String(r.id)===String(routineState.id)):null;
}
function routineElapsed(){
 if(!routineState)return 0;
 if(routineState.paused)return routineState.elapsedBeforeStep;
 return routineState.elapsedBeforeStep+(Date.now()-routineState.stepStarted);
}
function renderRunningSteps(){
 if(!routineState)return;
 const r=currentRoutine();if(!r)return;
 const step=r.steps[routineState.index];
 $("routineStepCount").textContent=(routineState.index+1)+"/"+r.steps.length;
 $("runningSteps").innerHTML=r.steps.map((s,i)=>`
  <div class="step">
   <div class="between"><span>${i+1}. ${esc(s.name)}</span><span class="small">${s.mins}分</span></div>
   <div class="small">${i===routineState.index?"実行中":i<routineState.index?"完了":"これから"}</div>
   ${i===routineState.index?'<button class="btn small primary" onclick="completeRoutineStep()">このステップを完了</button>':""}
  </div>
 `).join("");
 $("routineProgress").style.width=(routineState.index/r.steps.length*100)+"%";
 $("routineTimer").textContent=fmtTime(Math.floor(routineElapsed()/1000));
 $("runningTitle").textContent=r.name+"： "+step.name;
}
function completeRoutineStep(){
 if(!routineState)return;
 const r=currentRoutine();if(!r)return;
 const sec=Math.floor(routineElapsed()/1000);
 routineState.totalElapsed=(routineState.totalElapsed||0)+sec;
 routineState.index++;
 if(routineState.index>=r.steps.length){
  logSeconds(routineState.totalElapsed,"ルーティン",r.name);
  stopRoutine();toast("ルーティン完了！おつかれさま ♡");render();return;
 }
 routineState.elapsedBeforeStep=0;
 routineState.stepStarted=Date.now();
 renderRunningSteps();
}
function pauseRoutine(){
 if(!routineState)return;
 if(!routineState.paused){
  routineState.elapsedBeforeStep=routineElapsed();
  routineState.paused=true;
 }else{
  routineState.stepStarted=Date.now();
  routineState.paused=false;
 }
 renderRunningSteps();
}
function startRoutineInterval(){
 clearInterval(routineInterval);
 routineInterval=setInterval(()=>{
  if(routineState){
   $("routineTimer").textContent=fmtTime(Math.floor(routineElapsed()/1000));
  }
 },500);
}
function stopRoutine(){
 clearInterval(routineInterval);routineInterval=null;
 routineState=null;
 $("routineRunner").classList.add("hidden");
}

/* PREP */
let prepItems=[],prepPlan=[],prepEnd=0,prepInterval=null;
let prepRun=null;

function renderPrepRoutineOptions(){
 const select=$("prepRoutineSelect");
 const prev=select.value;
 select.innerHTML='<option value="">ルーティンを選んでください</option>';
 db.routines.forEach(r=>{
  const o=document.createElement("option");o.value=r.id;o.textContent=r.name;select.appendChild(o);
 });
 if(db.routines.some(r=>String(r.id)===String(prev)))select.value=prev;
}

function appendSelectedRoutineToPrep(){
 const id=$("prepRoutineSelect").value;
 const r=db.routines.find(x=>String(x.id)===String(id));
 if(!r)return toast("ルーティンを選んでください");
 const existing=new Set(prepItems.map(s=>s.name));
 const additions=r.steps.filter(s=>!existing.has(s.name)).map(s=>({
  id:uid(),name:s.name,mins:s.mins,priority:s.priority,include:true
 }));
 if(!additions.length)return toast("この項目は追加済みです");
 prepItems.push(...additions);
 renderPrepItems();toast("準備項目を追加しました");
}

function addPrepItem(){
 prepItems.push({id:uid(),name:"",mins:null,priority:"prefer",include:true});
 renderPrepItems();
}

function renderPrepItems(){
 $("prepItems").innerHTML=prepItems.length?prepItems.map((s,i)=>`
  <div class="step">
   <label>項目名</label>
   <input value="${esc(s.name)}" placeholder="準備すること" oninput="updatePrepItem(${i},'name',this.value)">
   <div class="grid2">
    <div><label>所要時間（分）</label><input type="number" min="1" value="${s.mins??""}" placeholder="分" oninput="updatePrepItem(${i},'mins',this.value)"></div>
    <div><label>優先度</label><select onchange="updatePrepItem(${i},'priority',this.value)">
     <option value="must" ${s.priority==="must"?"selected":""}>必須</option>
     <option value="prefer" ${s.priority==="prefer"?"selected":""}>できればやる</option>
     <option value="optional" ${s.priority==="optional"?"selected":""}>省略可能</option>
    </select></div>
   </div>
   <button class="btn small danger" onclick="removePrepItem(${i})">この項目を削除</button>
  </div>
 `).join(""):'<div class="empty">準備項目を追加してください。</div>';
}

function updatePrepItem(i,key,value){
 if(!prepItems[i])return;
 if(key==="mins")prepItems[i][key]=value===""?null:Number(value);
 else prepItems[i][key]=value;
}
function removePrepItem(i){prepItems.splice(i,1);renderPrepItems()}

function getLeaveDate(){
 const value=$("leaveTime").value;
 if(!value)return null;
 const [h,m]=value.split(":").map(Number);
 const now=new Date(),leave=new Date();
 leave.setHours(h,m,0,0);
 if(leave<=now)leave.setDate(leave.getDate()+1);
 return leave;
}

function planPrep(){
 const leave=getLeaveDate();
 if(!leave)return toast("出発時刻を入力してください");
 if(!prepItems.length)return toast("準備項目を追加してください");
 if(prepItems.some(s=>!s.name.trim()))return toast("項目名を入力してください");
 if(prepItems.some(s=>!Number.isFinite(s.mins)||s.mins<=0))return toast("各項目の時間を入力してください");

 const available=Math.max(0,Math.floor((leave-Date.now())/60000));
 $("prepRemaining").textContent=available+"分";
 const items=prepItems.map(s=>({...s,include:false}));
 let remaining=available;

 const must=items.filter(s=>s.priority==="must");
 const prefer=items.filter(s=>s.priority==="prefer");
 const optional=items.filter(s=>s.priority==="optional");

 must.forEach(s=>{s.include=true;remaining-=s.mins});
 prefer.forEach(s=>{
  if(s.mins<=remaining){s.include=true;remaining-=s.mins}
 });
 optional.forEach(s=>{
  if(s.mins<=remaining){s.include=true;remaining-=s.mins}
 });

 prepPlan=items;
 const mustTotal=must.reduce((a,s)=>a+s.mins,0);
 const selected=items.filter(s=>s.include);
 const total=selected.reduce((a,s)=>a+s.mins,0);
 let message="";
 if(mustTotal>available){
  message="必須の作業だけでも残り時間を超えています。時間を短縮するか、出発時刻を見直す必要があります。必須項目の時間は自動変更していません。";
 }else if(total<=available&&selected.length===items.length){
  message="すべての準備項目を実行できそうです。いつもの時間設定をそのまま使えます。";
 }else{
  message="残り時間に合わせて、優先度の高い項目から提案しました。チェックを変更して自分で調整できます。";
 }

 $("prepMessage").textContent=message;
 $("prepPlan").innerHTML=items.map((s,i)=>`
  <div class="prep-item">
   <label>
    <input type="checkbox" ${s.include?"checked":""} onchange="togglePrepPlan(${i},this.checked)">
    <span class="grow">
     <strong>${esc(s.name)}</strong>
     <div class="small">${s.mins}分 ・ ${priorityLabels[s.priority]}</div>
    </span>
   </label>
  </div>
 `).join("");
 $("prepResult").classList.remove("hidden");
 updatePrepTotal();
 prepEnd=leave.getTime();
}

function togglePrepPlan(i,checked){
 if(!prepPlan[i])return;
 if(prepPlan[i].priority==="must"&&!checked){
  if(!confirm("必須に設定された項目です。本当に外しますか？")){
   planPrep();return;
  }
 }
 prepPlan[i].include=checked;
 updatePrepTotal();
}

function updatePrepTotal(){
 const total=prepPlan.filter(s=>s.include).reduce((a,s)=>a+s.mins,0);
 $("prepTotal").textContent=total+"分";
 const leave=getLeaveDate();
 const available=leave?Math.max(0,Math.floor((leave-Date.now())/60000)):0;
 $("prepDifference").textContent=total>available?"予定時間を"+(total-available)+"分超えています。":(available-total)+"分の余裕があります。";
}

function acceptPrepPlan(){
 const selected=prepPlan.filter(s=>s.include);
 if(!selected.length)return toast("実行する項目を選んでください");
 const leave=getLeaveDate();
 if(!leave)return toast("出発時刻を確認してください");
 const available=Math.max(0,Math.floor((leave-Date.now())/60000));
 const total=selected.reduce((a,s)=>a+s.mins,0);
 if(total>available&&!confirm("選択した項目の合計時間が残り時間を超えています。それでも開始しますか？"))return;

 prepRun={items:selected.map(s=>({...s})),index:0,started:false,paused:false,elapsed:0,stepStarted:0,leaveAt:leave.getTime()};
 $("prepTimerName").textContent="今回の準備プラン";
 updatePrepRunner();
 toast("今回の準備プランをセットしました");
}

function updatePrepRunner(){
 if(!prepRun)return;
 const s=prepRun.items[prepRun.index];
 if(!s){$("prepCurrentStep").textContent="準備完了！";return}
 $("prepCurrentStep").textContent=(prepRun.index+1)+"/"+prepRun.items.length+"　"+s.name+"（"+s.mins+"分）";
 $("prepTimerName").textContent="今回の準備プラン";
}

function startPrepClock(){
 if(!prepRun){if(!prepPlan.length)return toast("先に準備プランを作ってください");acceptPrepPlan();if(!prepRun)return}
 if(prepRun.paused){
  prepRun.paused=false;prepRun.stepStarted=Date.now();
 }else if(!prepRun.started){
  prepRun.started=true;prepRun.stepStarted=Date.now();
 }
 clearInterval(prepInterval);
 prepInterval=setInterval(()=>{
  if(!prepRun||!prepRun.started||prepRun.paused)return;
  const total=prepRun.elapsed+(Date.now()-prepRun.stepStarted);
  $("prepClock").textContent=fmtTime(Math.floor(total/1000));
 },500);
 toast("準備タイマーを開始しました");
}

function pausePrepClock(){
 if(!prepRun||!prepRun.started)return;
 if(!prepRun.paused){
  prepRun.elapsed+=Date.now()-prepRun.stepStarted;
  prepRun.paused=true;
 }else{
  prepRun.paused=false;prepRun.stepStarted=Date.now();
 }
}
function nextPrepStep(){
 if(!prepRun)return;
 const elapsed=prepRun.started?prepRun.elapsed+(prepRun.paused?0:Date.now()-prepRun.stepStarted):0;
 logSeconds(Math.floor(elapsed/1000),"準備",prepRun.items[prepRun.index].name);
 prepRun.index++;prepRun.elapsed=0;prepRun.started=false;prepRun.paused=false;
 if(prepRun.index>=prepRun.items.length){
  stopPrepClock();prepRun=null;$("prepClock").textContent="00:00";
  $("prepCurrentStep").textContent="準備完了！";
  toast("準備完了！おつかれさま ♡");render();return;
 }
 $("prepClock").textContent="00:00";updatePrepRunner();
}
function stopPrepClock(){
 clearInterval(prepInterval);prepInterval=null;
 prepRun=null;$("prepClock").textContent="00:00";
 $("prepCurrentStep").textContent="タイマーを終了しました";
}

/* TASK TIMER */
let activeTask=null,taskInterval=null;
function startTaskTimer(id){
 const t=db.tasks.find(x=>String(x.id)===String(id));
 if(!t)return;
 if(activeTask){
  if(!confirm("計測中のタイマーを切り替えますか？"))return;
  stopTaskTimer(false);
 }
 activeTask={id:t.id,name:t.name,cat:t.cat,started:Date.now()};
 $("activeTimerCard").classList.remove("hidden");
 $("activeTimerName").textContent=t.name;
 showPage("tasks");
 clearInterval(taskInterval);
 taskInterval=setInterval(updateTaskClock,1000);updateTaskClock();
}
function updateTaskClock(){
 if(activeTask)$("activeTimerClock").textContent=fmtTime(Math.floor((Date.now()-activeTask.started)/1000));
}
function stopTaskTimer(shouldSave){
 clearInterval(taskInterval);taskInterval=null;
 if(activeTask&&shouldSave){
  logSeconds(Math.floor((Date.now()-activeTask.started)/1000),activeTask.cat,activeTask.name);
  toast("時間を記録しました");
 }
 activeTask=null;
 $("activeTimerCard").classList.add("hidden");
 render();
}

/* FOCUS TIMER */
let focusInterval=null,focusEnd=0;
function startFocus(){
 stopFocus(false);
 focusEnd=Date.now()+5*60*1000;
 focusInterval=setInterval(()=>{
  const rem=Math.max(0,Math.ceil((focusEnd-Date.now())/1000));
  $("focusClock").textContent=fmtTime(rem);
  if(rem<=0){
   clearInterval(focusInterval);focusInterval=null;
   logSeconds(300,"集中","5分集中");
   toast("5分間おつかれさま！");render();
  }
 },250);
 toast("5分集中スタート！");
}
function stopFocus(reset=true){
 clearInterval(focusInterval);focusInterval=null;
 if(reset)$("focusClock").textContent="05:00";
}

function logSeconds(sec,cat,name){
 if(sec<=0)return;
 if(!Array.isArray(db.records[dateKey()]))db.records[dateKey()]=[];
 db.records[dateKey()].push({sec:Math.max(0,Number(sec)||0),cat:cat||"その他",name:name||"",at:new Date().toISOString()});
 save();
}

/* REFLECTION */
function loadTodayReflection(){
 const r=db.reflection[dateKey()]||{};
 $("reflectionWin").value=r.win||"";
 $("reflectionBlock").value=r.block||"";
 $("reflectionNext").value=r.next||"";
 $("reflectionSaved").textContent=r.saved?"今日の振り返りは保存済み ♡":"";
}
function saveReflection(){
 db.reflection[dateKey()]={
  win:$("reflectionWin").value,
  block:$("reflectionBlock").value,
  next:$("reflectionNext").value,
  saved:true,updatedAt:new Date().toISOString()
 };
 save();$("reflectionSaved").textContent="保存しました ♡";
 renderReview();toast("振り返りを保存しました");
}
let historyOpen=false;
function toggleReflectionHistory(){
 historyOpen=!historyOpen;
 $("reflectionHistory").classList.toggle("hidden",!historyOpen);
 $("historyToggle").textContent=historyOpen?"履歴を閉じる":"履歴を見る";
 if(historyOpen)renderReflectionHistory();
}
function renderReflectionHistory(){
 const el=$("reflectionHistory");if(!el)return;
 const entries=Object.entries(db.reflection||{}).filter(([k,r])=>k!==dateKey()&&r&&r.saved).sort((a,b)=>b[0].localeCompare(a[0]));
 if(!entries.length){el.innerHTML='<div class="empty">まだ過去の振り返りはありません。</div>';return}
 el.innerHTML=entries.map(([k,r])=>`
  <details class="history-entry">
   <summary>${esc(k)}</summary>
   <label>できたこと</label><textarea id="hist-win-${esc(k)}">${esc(r.win||"")}</textarea>
   <label>困ったこと</label><textarea id="hist-block-${esc(k)}">${esc(r.block||"")}</textarea>
   <label>明日やりたいこと</label><textarea id="hist-next-${esc(k)}">${esc(r.next||"")}</textarea>
   <button class="btn primary small" onclick="updateOldReflection('${esc(k)}')">この記録を更新</button>
  </details>
 `).join("");
}
function updateOldReflection(k){
 const r=db.reflection[k];if(!r)return;
 const a=$("hist-win-"+k),b=$("hist-block-"+k),c=$("hist-next-"+k);
 if(!a||!b||!c)return;
 db.reflection[k]={...r,win:a.value,block:b.value,next:c.value,updatedAt:new Date().toISOString()};
 save();toast("過去の記録を更新しました");
}
function renderReview(){
 $("reviewDone").textContent=todayTasks().filter(t=>t.done).length;
 $("reviewTime").textContent=minutesText(todaySeconds());
 if(historyOpen)renderReflectionHistory();
}

/* SETTINGS */
function changeTheme(theme){db.theme=theme;save();applyTheme();toast("テーマを変更しました")}
function exportData(){
 save();
 const blob=new Blob([JSON.stringify(db,null,2)],{type:"application/json"});
 const url=URL.createObjectURL(blob);
 const a=document.createElement("a");
 a.href=url;a.download="FLOW-backup-"+dateKey()+".json";
 document.body.appendChild(a);a.click();a.remove();
 setTimeout(()=>URL.revokeObjectURL(url),1000);
 toast("バックアップを作成しました");
}
function importData(){
 const file=$("importFile").files[0];
 if(!file)return toast("バックアップファイルを選んでください");
 if(!confirm("現在のデータを、選択したバックアップの内容に置き換えますか？"))return;
 const reader=new FileReader();
 reader.onload=()=>{
  try{
   const parsed=JSON.parse(reader.result);
   if(!parsed||typeof parsed!=="object"||Array.isArray(parsed))throw Error("invalid");
   db=normalize(parsed);save();
   historyOpen=false;$("reflectionHistory").classList.add("hidden");
   cancelRoutineEdit();render();loadTodayReflection();
   toast("バックアップを復元しました");
  }catch(e){toast("ファイルを読み込めませんでした。FLOWのバックアップか確認してください")}
 };
 reader.onerror=()=>toast("ファイルを読み込めませんでした");
 reader.readAsText(file);
}
function resetApp(){
 if(!confirm("本当に初期化しますか？先にバックアップを取ってください。"))return;
 if(!confirm("タスク・目標・記録・振り返りを含めて初期化します。続けますか？"))return;
 stopTaskTimer(false);stopRoutine();stopFocus(false);stopPrepClock();
 db=fresh();save();historyOpen=false;
 $("reflectionHistory").classList.add("hidden");
 prepItems=[];renderPrepItems();cancelRoutineEdit();
 render();loadTodayReflection();showPage("home");
 toast("初期化しました");
}

/* INITIALIZE */
function dailyMaintenance(){
 if(!db.dailyTasks)db.dailyTasks={};
 if(!db.dailyTasks[dateKey()])db.dailyTasks[dateKey()]={};
}
dailyMaintenance();
save();
render();
loadTodayReflection();
renderPrepItems();
</script>
</body>
</html>
