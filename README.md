<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#f5f0e8">
<title>FLOW</title>
<style>
:root{--bg:#f7f3ed;--paper:#fffdf9;--ink:#403b38;--muted:#8c827a;--accent:#b8a5c9;--soft:#eee6f4;--line:#e9e1d8;--good:#849d85;--danger:#bc7777}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--ink);font-family:-apple-system,BlinkMacSystemFont,"Hiragino Sans","Yu Gothic",sans-serif;font-size:15px;line-height:1.65}button,input,textarea,select{font:inherit}button{cursor:pointer}.app{max-width:720px;margin:auto;padding:18px 15px 105px}header{padding:12px 3px 18px}.eyebrow{font-size:11px;letter-spacing:2px;color:var(--muted)}h1{font-size:29px;margin:2px 0;font-weight:750}h2{font-size:17px;margin:0 0 12px}h3{font-size:14px;margin:0 0 7px}p{margin:7px 0}.small{font-size:12px;color:var(--muted)}.muted{color:var(--muted)}.page{display:none}.page.active{display:block}.card{background:var(--paper);border:1px solid var(--line);border-radius:18px;padding:17px;margin:13px 0;box-shadow:0 4px 18px #40352b08}.row{display:flex;align-items:center;gap:9px}.between{display:flex;align-items:center;justify-content:space-between;gap:10px}.wrap{flex-wrap:wrap}.grow{flex:1;min-width:0}.btn{border:1px solid var(--line);border-radius:12px;padding:9px 12px;background:white;color:var(--ink)}.btn.primary{background:var(--soft);border-color:var(--soft)}.btn.dark{background:var(--ink);color:white}.btn.small{font-size:12px;padding:6px 9px}.btn.danger{color:var(--danger)}input,textarea,select{width:100%;border:1px solid var(--line);border-radius:10px;padding:10px;background:white;color:var(--ink);margin:4px 0 10px}textarea{min-height:78px;resize:vertical}label{display:block;font-size:12px;color:var(--muted)}.grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px}.stat{background:var(--soft);border-radius:14px;padding:12px}.big{font-size:28px;font-weight:750}.progress{height:7px;border-radius:10px;background:#eee8e1;overflow:hidden;margin:10px 0}.progress span{display:block;height:100%;background:var(--accent);border-radius:10px}.pill{display:inline-block;background:#f2ede6;border-radius:20px;padding:3px 8px;font-size:11px;color:var(--muted)}.task{display:flex;gap:10px;align-items:flex-start;border-bottom:1px solid var(--line);padding:11px 0}.task:last-child{border-bottom:0}.task input[type=checkbox]{width:21px;height:21px;margin:4px 0 0;accent-color:var(--accent);flex-shrink:0}.task.done .task-name{text-decoration:line-through;color:var(--muted)}.empty{text-align:center;padding:17px;color:var(--muted);font-size:13px}.nav{position:fixed;z-index:5;bottom:0;left:0;right:0;display:flex;justify-content:center;gap:3px;background:#fffdf9f5;border-top:1px solid var(--line);padding:7px 3px max(8px,env(safe-area-inset-bottom));backdrop-filter:blur(12px)}.nav button{flex:1;max-width:105px;border:0;background:transparent;color:var(--muted);border-radius:11px;padding:7px 1px;font-size:11px}.nav button span{display:block;font-size:19px;line-height:1.3}.nav button.active{background:var(--soft);color:var(--ink)}.timer{text-align:center;padding:16px 0;font-size:43px;font-weight:750;font-variant-numeric:tabular-nums}.step{padding:9px 0;border-bottom:1px solid var(--line)}.history-entry{background:#faf7f2;border-radius:12px;padding:12px;margin-top:10px}hr{border:0;border-top:1px solid var(--line);margin:15px 0}.hidden{display:none!important}.toast{position:fixed;z-index:20;bottom:95px;left:50%;transform:translateX(-50%);background:var(--ink);color:white;padding:9px 15px;border-radius:20px;font-size:13px;display:none;max-width:90%}.guide details{border-bottom:1px solid var(--line);padding:10px 0}.guide details:last-child{border-bottom:0}.guide summary{font-weight:700;cursor:pointer;padding:3px 0}.guide ul{padding-left:22px}.guide li{margin:5px 0}.guide-note{background:#faf7f2;border-radius:12px;padding:12px;margin-top:12px}.nav button{min-width:0}@media(max-width:390px){.nav{gap:0}.nav button{font-size:10px}.nav button span{font-size:17px}.btn{padding:8px 10px}}@media(min-width:600px){.app{padding-top:28px}}
</style>
</head>
<body>
<div class="app">
<header><div class="eyebrow">MY LITTLE DAILY NOTE</div><h1>FLOW ♡</h1><div class="small" id="todayLabel"></div></header>

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
<div class="card"><div class="between"><h2>今日のタスク</h2><button class="btn small" onclick="showPage('tasks')">すべて見る →</button></div><div id="homeTasks"></div></div>
<div class="card"><h2>わたしの目標</h2><div id="homeGoals"></div><button class="btn primary" onclick="showPage('goals')">目標を確認する</button></div>
<div class="card"><h2>今日の振り返り</h2><p class="small">今日の自分に、少しだけ目を向けてみよう。</p><button class="btn primary" onclick="showPage('review')">振り返りを書く ♡</button></div>
</section>

<section class="page" id="page-tasks">
<div class="card"><div class="between"><h2>今日のタスク</h2><span class="pill" id="taskCounter">0件</span></div><p class="small">チェックは日付ごとに保存。翌日には新しい日のチェックになります。</p><div id="taskList"></div></div>
<div class="card">
<h2>タスクを追加</h2>
<label for="taskName">やること</label><input id="taskName" placeholder="例：英単語を覚える">
<div class="grid2">
<div><label for="taskMins">予定時間（分）</label><input id="taskMins" type="number" min="1" value="15"></div>
<div><label for="taskCat">カテゴリー</label><select id="taskCat"><option>勉強</option><option>学校</option><option>生活</option><option>運動</option><option>美容</option><option>その他</option></select></div>
</div>
<label for="taskGoal">関連する目標</label><select id="taskGoal"></select>
<button class="btn primary" onclick="addTask()">＋ タスクを追加</button>
</div>
</section>

<section class="page" id="page-goals">
<div class="card"><h2>わたしの目標</h2><p class="small">目標を毎日の行動につなげよう。</p><div id="goalList"></div></div>
<div class="card"><h2>新しい目標</h2><label for="goalName">目標</label><input id="goalName" placeholder="例：看護学校に合格する"><label for="goalWhy">達成したい理由（任意）</label><textarea id="goalWhy" placeholder="どんな自分になりたい？"></textarea><button class="btn primary" onclick="addGoal()">＋ 目標を追加</button></div>
</section>

<section class="page" id="page-routines">
<div class="card"><h2>わたしのルーティン</h2><p class="small">朝の準備や寝る前の習慣を登録できます。最大3つです。</p><div id="routineList"></div></div>
<div class="card"><h2>ルーティンを作る</h2><label for="routineName">ルーティン名</label><input id="routineName" placeholder="例：学校に行く準備"><label for="routineSteps">手順（1行に1つ）</label><textarea id="routineSteps" placeholder="顔を洗う&#10;着替える&#10;朝ごはんを食べる&#10;持ち物を確認する"></textarea><label for="routineMins">各手順の目安時間（分）</label><input id="routineMins" type="number" min="1" value="5"><button class="btn primary" onclick="addRoutine()">＋ ルーティンを保存</button></div>
<div class="card hidden" id="routineRunner"><div class="between"><h2 id="runningTitle">ルーティン実行中</h2><span class="pill" id="routineStepCount"></span></div><div class="timer" id="routineTimer">00:00</div><div class="progress"><span id="routineProgress" style="width:0%"></span></div><div id="runningSteps"></div><button class="btn" onclick="stopRoutine()">中断する</button></div>
</section>

<section class="page" id="page-prep">
<div class="card">
<h2>お出かけ準備タイマー</h2><p class="small">出発時間と準備を整理しましょう。</p>
<label for="leaveTime">出発時刻</label><input type="time" id="leaveTime" value="08:00">
<div style="background:#faf7f2;border:1px solid var(--line);border-radius:13px;padding:13px;margin:8px 0 14px">
<h3>♡ 登録済みルーティンから追加</h3><p class="small">いつものルーティンを準備項目に追加できます。追加したあとに、項目を編集することもできます。</p>
<label for="prepRoutineSelect">追加するルーティン</label><select id="prepRoutineSelect"><option value="">ルーティンを選んでください</option></select>
<button class="btn" type="button" onclick="appendSelectedRoutineToPrep()">＋ 選んだルーティンを準備項目に追加</button>
<div class="small" id="prepRoutineMessage">ルーティンをまだ登録していない場合は、自由入力だけでも使えます。</div>
</div>
<label for="prepTasks">準備すること（1行に1つ）</label><textarea id="prepTasks" placeholder="着替える&#10;顔を洗う&#10;髪を整える&#10;持ち物を確認する"></textarea>
<p class="small">ルーティンを追加したあとでも、ここに直接入力・編集できます。</p>
<button class="btn primary" onclick="planPrep()">準備プランを作る</button>
</div>
<div class="card hidden" id="prepResult"><div class="between"><h2>準備プラン</h2><span class="pill" id="prepRemaining"></span></div><div id="prepPlan"></div><div class="timer" id="prepClock">--:--</div><button class="btn dark" onclick="startPrepClock()">タイマー開始</button><button class="btn" onclick="stopPrepClock()">停止</button></div>
<div class="card"><h2>5分だけ集中</h2><p class="small">まずは5分だけ始めてみましょう。</p><div class="timer" id="focusClock">05:00</div><button class="btn primary" onclick="startFocus()">スタート</button><button class="btn" onclick="stopFocus()">停止・リセット</button></div>
</section>

<section class="page" id="page-review">
<div class="card"><h2>今日の振り返り</h2><p class="small">できたことも、うまくいかなかったことも、次に活かすための記録です。</p>
<label for="reflectionWin">今日できたこと・頑張ったこと</label><textarea id="reflectionWin" placeholder="小さなことでも大丈夫です"></textarea>
<label for="reflectionBlock">困ったこと・改善したいこと</label><textarea id="reflectionBlock" placeholder="次に工夫できそうなことは？"></textarea>
<label for="reflectionNext">明日やりたいこと</label><textarea id="reflectionNext" placeholder="明日の自分へのメモ"></textarea>
<button class="btn primary" onclick="saveReflection()">今日の振り返りを保存</button><p class="small" id="reflectionSaved"></p>
</div>
<div class="card"><div class="between"><h2>過去の振り返り</h2><button class="btn small" id="historyToggle" onclick="toggleReflectionHistory()">履歴を見る</button></div><p class="small">普段は閉じておき、読み返したいときだけ開けます。</p><div id="reflectionHistory" class="hidden"></div></div>
<div class="card"><h2>今日の記録</h2><div class="grid2"><div class="stat"><div class="small">完了したタスク</div><div class="big" id="reviewDone">0</div></div><div class="stat"><div class="small">集中した時間</div><div class="big" id="reviewTime">0分</div></div></div></div>
</section>

<section class="page" id="page-settings">
<div class="card"><h2>FLOWの設定</h2><label for="themeChoice">テーマ</label><select id="themeChoice" onchange="changeTheme(this.value)"><option value="beige">ミルクベージュ</option><option value="lavender">ラベンダー × 白</option><option value="mono">モノトーン</option></select></div>
<div class="card"><h2>使い方・ガイド</h2><p class="small">各機能の使い方、データの保存、困ったときの対処方法を確認できます。</p><button class="btn primary" onclick="showPage('guide')">使い方・ガイドを読む →</button></div>
<div class="card"><h2>データのバックアップ</h2><p class="small">タスク・目標・ルーティン・記録・振り返りをJSONファイルに保存できます。</p><button class="btn primary" onclick="exportData()">バックアップを書き出す</button><hr><label for="importFile">バックアップファイルから復元</label><input type="file" id="importFile" accept=".json,application/json"><button class="btn" onclick="importData()">バックアップを復元</button></div>
<div class="card"><h2>保存について</h2><p class="small">データはこのブラウザ内に保存されます。ブラウザのデータ削除や別の端末への変更に備えて、定期的にバックアップしてください。</p><hr><button class="btn danger" onclick="resetApp()">アプリのデータを初期化</button></div>
</section>

<section class="page" id="page-guide">
<div class="card">
<div class="between"><h2>使い方・ガイド</h2><button class="btn small" onclick="showPage('settings')">← 設定へ戻る</button></div>
<p>FLOWを無理なく使うためのガイドです。必要な項目を開いて確認してください。</p>
<div class="guide">
<details open><summary>1. FLOWでできること</summary><p>FLOWは、目標を日々のタスクにつなげ、ルーティンや準備時間を整理し、振り返りを残すためのアプリです。すべてを完璧にこなすことより、今の自分に合う小さな一歩を続けることを大切にしてください。</p></details>
<details><summary>2. 最初にすること</summary><ol><li>「目標」で、今大切にしたい目標を確認・追加します。</li><li>「タスク」で、今日取り組む行動と目安時間を登録します。</li><li>毎朝の支度など繰り返す行動は「ルーティン」に登録します。</li><li>出かける前は「準備」で出発時刻と準備項目を整理します。</li><li>一日の終わりに「振り返り」を保存します。</li></ol></details>
<details><summary>3. ホームと達成率</summary><p>ホームでは、今日のタスク数、完了数、残りのタスク、記録時間、目標を確認できます。達成率は「今日完了したタスク数 ÷ 今日のタスク総数」で計算します。タスクが0件の場合は0%と表示されます。達成率は自分を評価する点数ではなく、今日の進み具合を把握する目安として使ってください。</p></details>
<details><summary>4. タスクの追加・完了・削除</summary><ul><li>「タスク」ページで、やること・目安時間・カテゴリーを設定して追加します。</li><li>必要に応じて目標と関連づけられます。関連づけても、タスクの完了だけで目標が自動達成になるわけではありません。</li><li>チェックを入れると、その日付のタスク完了として保存されます。翌日は新しい日のチェックになります。</li><li>削除したタスクは一覧からなくなります。削除前に内容を確認してください。</li><li>「計測」を押すと、そのタスクに取り組んだ時間を計測できます。「計測終了・記録」で記録します。</li></ul></details>
<details><summary>5. 目標の使い方</summary><p>目標名と、必要であれば達成したい理由を入力して追加します。「達成にする」で達成済みにできます。目標を削除すると一覧からなくなります。目標に関連するタスクは目標ページで確認できます。</p></details>
<details><summary>6. ルーティンの作り方と実行</summary><ul><li>ルーティン名を入力し、手順を1行に1つずつ入力して保存します。</li><li>現在、登録できるルーティンは最大3つです。各手順の目安時間は、作成時に設定した同じ時間が入ります。</li><li>「開始」を押し、終わった手順の「完了にする」を押して進めます。</li><li>上部の時計は、ルーティン開始からの経過時間を表示します。手順ごとの制限時間を知らせるカウントダウンではありません。</li><li>最後まで完了すると、経過時間が記録されます。途中で「中断する」を押した場合は、完了記録にはなりません。</li></ul></details>
<details><summary>7. 出発前の準備プラン</summary><ul><li>「準備」で出発時刻を設定します。</li><li>登録済みルーティンを選んで追加するか、準備項目を1行に1つずつ入力します。追加後も自由に編集できます。</li><li>「準備プランを作る」を押すと、出発までの残り時間を項目数で均等に分けた目安が表示されます。各項目にかかる実際の時間を自動予測する機能ではありません。</li><li>設定した時刻がすでに過ぎている場合は、次の日の同じ時刻を出発時刻として扱います。</li><li>「タイマー開始」で出発までの残り時間を確認し、「停止」でタイマーを止められます。</li><li>出発時刻や準備項目は、このバージョンでは画面を再読み込みすると初期表示に戻る場合があります。必要な内容はメモにも残してください。</li></ul></details>
<details><summary>8. 5分だけ集中タイマー</summary><p>「スタート」で5分間のタイマーが始まります。5分が終わると、集中した300秒が記録されます。途中で「停止・リセット」を押した場合、途中までの時間は記録されず、表示は05:00に戻ります。</p></details>
<details><summary>9. 振り返りと過去の記録</summary><ul><li>「今日できたこと」「困ったこと」「明日やりたいこと」を入力し、「今日の振り返りを保存」を押します。</li><li>保存ボタンを押す前の内容は、保存済みとは限りません。入力後は保存を確認してください。</li><li>過去の記録は「履歴を見る」で開けます。読み返したいときだけ開いておけます。</li><li>過去の内容を変更した場合は、その記録内の「この記録を更新」を押してください。</li></ul></details>
<details><summary>10. テーマの変更</summary><p>「設定」のテーマから、ミルクベージュ、ラベンダー × 白、モノトーンを選べます。テーマの変更は保存され、次回も選んだテーマが適用されます。</p></details>
<details><summary>11. バックアップと復元</summary><ul><li>「バックアップを書き出す」で、データをJSONファイルとして保存します。</li><li>ファイルを保存した場所は、端末やブラウザによって異なります。ファイルアプリやダウンロード一覧を確認してください。</li><li>復元すると、現在のアプリデータが選んだバックアップの内容に置き換わります。復元前に、現在のデータもバックアップすることをおすすめします。</li><li>バックアップには個人的な振り返りなどが含まれることがあります。共有先に注意して、大切に保管してください。</li></ul></details>
<details><summary>12. データ保存とプライバシー</summary><p>データは、このアプリを開いているブラウザのローカル保存領域に保存されます。自動で別の端末に同期される仕組みではありません。ブラウザのサイトデータ削除、プライベートブラウズの利用、ブラウザや端末の変更などでデータが失われる可能性があります。大切な記録は定期的にバックアップしてください。</p></details>
<details><summary>13. 初期化するとき</summary><p>「アプリのデータを初期化」を押すと確認が2回表示されます。続行すると、目標・タスク・ルーティン・記録・振り返りなどが初期状態に戻ります。元に戻せない場合があるため、必要なデータは先にバックアップしてください。</p></details>
<details><summary>14. うまく動かないとき</summary><ul><li>表示が更新されない場合は、画面を再読み込みしてみてください。</li><li>データが消えたように見える場合は、以前使っていたブラウザ・端末で開いていないか確認してください。</li><li>タイマーは、ページを閉じたりブラウザを終了したりすると、動作や記録が期待どおりにならない場合があります。計測中はページを開いたままにしてください。</li><li>復元に失敗する場合は、FLOWから書き出したJSONファイルを選んでいるか確認してください。</li><li>それでも解決しない場合は、データを初期化する前に、バックアップがあるか確認してください。</li></ul></details>
</div>
<div class="guide-note"><strong>大切なお知らせ</strong><p>FLOWは日々を整理するための補助ツールです。予定どおりに進まない日があっても問題ありません。必要に応じてタスクを調整し、自分のペースで使ってください。</p></div>
<button class="btn primary" style="margin-top:12px" onclick="showPage('settings')">設定に戻る</button>
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
const STORE="FLOW_APP_V2",LEGACY="FLOW_COMPLETE_V1",$=id=>document.getElementById(id),uid=()=>Date.now().toString(36)+Math.random().toString(36).slice(2,8),dateKey=(d=new Date())=>d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0"),esc=s=>String(s??"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const fresh=()=>({version:2,theme:"beige",mood:"ふつう",goals:[{id:uid(),name:"看護学校に合格する",why:"自分の目標に向かって進む",done:false},{id:uid(),name:"体力をつける",why:"毎日を元気に過ごす",done:false},{id:uid(),name:"毎日英単語を覚える",why:"少しずつ積み重ねる",done:false}],tasks:[],routines:[],schedules:[],records:{},reflection:{},dailyTasks:{},active:null,runningRoutine:null});
function normalize(x){const f=fresh();x=x&&typeof x==="object"?x:{};const tasks=Array.isArray(x.tasks)?x.tasks.map((t,i)=>({...t,id:t.id||uid(),name:t.name||"やること",cat:t.cat||"その他",mins:Math.max(1,Number(t.mins??t.estimate??15)||15),priority:Number(t.priority||1),goalId:t.goalId||"",done:!!t.done,deferred:!!t.deferred,order:Number(t.order??i)})):[];const dailyTasks=x.dailyTasks&&typeof x.dailyTasks==="object"?x.dailyTasks:{};if(!x.dailyTasks){dailyTasks[dateKey()]={};tasks.forEach(t=>{if(t.done)dailyTasks[dateKey()][String(t.id)]=true})}const routines=(Array.isArray(x.routines)?x.routines:f.routines).slice(0,3).map(r=>({...r,id:r.id||uid(),name:r.name||"ルーティン",icon:r.icon||"↻",steps:(r.steps||[]).map(s=>typeof s==="string"?{id:uid(),name:s,mins:5,done:false}:{...s,id:s.id||uid(),name:s.name||"ステップ",mins:Math.max(1,Number(s.mins??s.min??5)||5),done:false})}));return {...f,...x,tasks,routines,goals:(Array.isArray(x.goals)?x.goals:f.goals).map(g=>({...g,id:g.id||uid()})),dailyTasks,records:x.records&&typeof x.records==="object"?x.records:{},reflection:x.reflection&&typeof x.reflection==="object"?x.reflection:{},theme:x.theme||"beige",active:null,runningRoutine:null}}
function loadDB(){try{let raw=localStorage.getItem(STORE);if(!raw)raw=localStorage.getItem(LEGACY);if(raw)return normalize(JSON.parse(raw))}catch(e){console.warn("FLOW data could not be read",e)}return fresh()}
let db=loadDB();
function save(){try{localStorage.setItem(STORE,JSON.stringify(db))}catch(e){toast("保存できませんでした。バックアップを確認してください。")}}
function toast(msg){const el=$("toast");el.textContent=msg;el.style.display="block";clearTimeout(toast.timer);toast.timer=setTimeout(()=>el.style.display="none",2400)}
function taskDone(id,k=dateKey()){return !!db.dailyTasks?.[k]?.[String(id)]}
function setTaskDone(id,value,k=dateKey()){if(!db.dailyTasks)db.dailyTasks={};if(!db.dailyTasks[k])db.dailyTasks[k]={};db.dailyTasks[k][String(id)]=!!value;save()}
function todayTasks(){return db.tasks.map(t=>({...t,done:taskDone(t.id)}))}
function todaySeconds(){return (db.records[dateKey()]||[]).reduce((a,r)=>a+Number(r.sec||0),0)}
function fmtTime(sec){sec=Math.max(0,Math.floor(sec));return String(Math.floor(sec/60)).padStart(2,"0")+":"+String(sec%60).padStart(2,"0")}
function minutesText(sec){const n=Math.round(sec/60);return n<60?n+"分":Math.floor(n/60)+"時間"+(n%60?n%60+"分":"")}
function showPage(name){document.querySelectorAll(".page").forEach(p=>p.classList.toggle("active",p.id==="page-"+name));document.querySelectorAll(".nav button").forEach(b=>b.classList.toggle("active",b.dataset.page===name));if(name==="review")loadTodayReflection();render();window.scrollTo({top:0,behavior:"smooth"})}
function render(){applyTheme();$("todayLabel").textContent=new Date().toLocaleDateString("ja-JP",{year:"numeric",month:"long",day:"numeric",weekday:"long"});renderHome();renderTasks();renderGoals();renderRoutines();renderPrepRoutineOptions();renderReview()}
function applyTheme(){const themes={beige:["#f7f3ed","#fffdf9","#403b38","#8c827a","#b8a5c9","#eee6f4","#e9e1d8"],lavender:["#f5f1fa","#fffefe","#393440","#898092","#b8a2d5","#eee5f8","#e8dfef"],mono:["#f1f1f1","#ffffff","#292929","#777777","#777777","#e7e7e7","#dddddd"]};const t=themes[db.theme]||themes.beige;["--bg","--paper","--ink","--muted","--accent","--soft","--line"].forEach((k,i)=>document.documentElement.style.setProperty(k,t[i]));if($("themeChoice"))$("themeChoice").value=db.theme}
function renderHome(){const ts=todayTasks(),done=ts.filter(t=>t.done).length,total=ts.length,pct=total?Math.round(done/total*100):0;$("homePercent").textContent=pct+"%";$("homeCount").textContent=done+" / "+total;$("homeProgress").style.width=pct+"%";$("remaining").textContent=total-done;$("todayTime").textContent=minutesText(todaySeconds());$("homeMessage").textContent=total&&done===total?"今日もよく頑張りました！ ♡":done?"いい感じ！少しずつ進んでいます。":"小さな一歩から始めましょう。";$("homeTasks").innerHTML=ts.length?ts.slice(0,5).map(taskHTML).join(""):'<div class="empty">タスクを追加してみましょう ♡</div>';$("homeGoals").innerHTML=db.goals.length?db.goals.filter(g=>!g.done).slice(0,3).map(g=>`<div class="step">☆ ${esc(g.name)}</div>`).join(""):'<div class="empty">目標を追加してみましょう</div>'}
function taskHTML(t){const id=String(t.id).replace(/\\/g,"\\\\").replace(/'/g,"\\'");return `<div class="task ${t.done?"done":""}"><input aria-label="${esc(t.name)}を完了" type="checkbox" ${t.done?"checked":""} onchange="toggleTask('${id}',this.checked)"><div class="grow"><div class="task-name">${esc(t.name)}</div><div class="small">${esc(t.cat)} ・ ${Number(t.mins)||0}分</div></div><button class="btn small" onclick="startTaskTimer('${id}')">計測</button><button class="btn small danger" onclick="deleteTask('${id}')">削除</button></div>`}
function renderTasks(){const ts=todayTasks().sort((a,b)=>a.order-b.order);$("taskCounter").textContent=ts.filter(t=>t.done).length+"/"+ts.length+"件";$("taskList").innerHTML=ts.length?ts.map(taskHTML).join(""):'<div class="empty">まだタスクがありません。下から追加してください。</div>';$("taskGoal").innerHTML='<option value="">目標と関連づけない</option>'+db.goals.map(g=>`<option value="${esc(g.id)}">${esc(g.name)}</option>`).join("")}
function toggleTask(id,checked){setTaskDone(id,checked);render();toast(checked?"タスク完了！おつかれさま ♡":"チェックを戻しました")}
function addTask(){const name=$("taskName").value.trim();if(!name)return toast("タスク名を入力してください");db.tasks.push({id:uid(),name,cat:$("taskCat").value,mins:Math.max(1,Number($("taskMins").value)||15),goalId:$("taskGoal").value,priority:1,done:false,order:db.tasks.length});$("taskName").value="";save();render();toast("タスクを追加しました")}
function deleteTask(id){if(!confirm("このタスクを削除しますか？"))return;db.tasks=db.tasks.filter(t=>String(t.id)!==String(id));save();render()}
function addGoal(){const name=$("goalName").value.trim();if(!name)return toast("目標を入力してください");db.goals.push({id:uid(),name,why:$("goalWhy").value.trim(),done:false});$("goalName").value="";$("goalWhy").value="";save();render();toast("目標を追加しました")}
function renderGoals(){$("goalList").innerHTML=db.goals.length?db.goals.map(g=>{const related=db.tasks.filter(t=>String(t.goalId)===String(g.id));return `<div class="step"><div class="between"><strong>${esc(g.name)}</strong><button class="btn small" onclick="toggleGoal('${esc(g.id)}')">${g.done?"達成済み ✓":"達成にする"}</button></div>${g.why?`<div class="small">${esc(g.why)}</div>`:""}<div class="small">関連タスク：${related.length}件</div>${related.map(t=>`<div class="small">・${esc(t.name)}${taskDone(t.id)?" ✓":""}</div>`).join("")}<button class="btn small danger" style="margin-top:7px" onclick="deleteGoal('${esc(g.id)}')">削除</button></div>`}).join(""):'<div class="empty">目標を追加してみましょう。</div>'}
function toggleGoal(id){const g=db.goals.find(x=>String(x.id)===String(id));if(g)g.done=!g.done;save();render()}
function deleteGoal(id){if(!confirm("この目標を削除しますか？"))return;db.goals=db.goals.filter(g=>String(g.id)!==String(id));save();render()}
function addRoutine(){const name=$("routineName").value.trim(),lines=$("routineSteps").value.split("\n").map(s=>s.trim()).filter(Boolean);if(!name||!lines.length)return toast("名前と手順を入力してください");if(db.routines.length>=3)return toast("ルーティンは最大3つまでです");const mins=Math.max(1,Number($("routineMins").value)||5);db.routines.push({id:uid(),name,steps:lines.map(s=>({id:uid(),name:s,mins,done:false}))});$("routineName").value="";$("routineSteps").value="";save();render();toast("ルーティンを保存しました")}
let routineState=null,routineInterval=null;
function renderRoutines(){$("routineList").innerHTML=db.routines.length?db.routines.map(r=>`<div class="step"><div class="between"><strong>${esc(r.name)}</strong><div class="row"><button class="btn small primary" onclick="startRoutine('${esc(r.id)}')">開始</button><button class="btn small danger" onclick="deleteRoutine('${esc(r.id)}')">削除</button></div></div>${r.steps.map((s,i)=>`<div class="small">${i+1}. ${esc(s.name)} ・ ${s.mins}分</div>`).join("")}</div>`).join(""):'<div class="empty">ルーティンを作ってみましょう。</div>';if(routineState)renderRunningSteps()}
function renderPrepRoutineOptions(){const select=$("prepRoutineSelect");if(!select)return;const prev=select.value;select.innerHTML='<option value="">ルーティンを選んでください</option>';if(!db.routines.length){$("prepRoutineMessage").textContent="ルーティンをまだ登録していない場合は、自由入力だけでも使えます。";return}db.routines.forEach(r=>{const o=document.createElement("option");o.value=String(r.id);o.textContent=r.name;select.appendChild(o)});if(db.routines.some(r=>String(r.id)===prev))select.value=prev;$("prepRoutineMessage").textContent="選んだルーティンの手順を、下の準備項目に追加します。"}
function appendSelectedRoutineToPrep(){const id=$("prepRoutineSelect").value;if(!id)return toast("追加したいルーティンを選んでください");const r=db.routines.find(x=>String(x.id)===String(id));if(!r){renderPrepRoutineOptions();return toast("ルーティンが見つかりませんでした")}const lines=$("prepTasks").value.split("\n").map(s=>s.trim()).filter(Boolean),existing=new Set(lines),add=r.steps.map(s=>String(typeof s==="string"?s:s.name||"").trim()).filter(s=>s&&!existing.has(s));if(!add.length)return toast("このルーティンの項目は追加済みです");$("prepTasks").value=lines.length?lines.join("\n")+"\n"+add.join("\n"):add.join("\n");$("prepRoutineMessage").textContent+=" 「"+r.name+"」から"+add.length+"項目を追加しました。";toast("ルーティンの項目を追加しました ♡")}
function startRoutine(id){const r=db.routines.find(x=>String(x.id)===String(id));if(!r||!r.steps.length)return;stopRoutine();routineState={id:r.id,index:0,started:Date.now(),elapsedBeforeStep:0,stepStarted:Date.now()};$("routineRunner").classList.remove("hidden");$("runningTitle").textContent=r.name;renderRunningSteps();startRoutineInterval();showPage("routines")}
function renderRunningSteps(){if(!routineState)return;const r=db.routines.find(x=>String(x.id)===String(routineState.id));if(!r)return;$("routineStepCount").textContent=Math.min(routineState.index+1,r.steps.length)+"/"+r.steps.length;$("runningSteps").innerHTML=r.steps.map((s,i)=>`<div class="step"><div class="between"><span>${i+1}. ${esc(s.name)}</span><button class="btn small ${i<routineState.index?"primary":""}" onclick="completeRoutineStep(${i})">${i<routineState.index?"完了 ✓":i===routineState.index?"完了にする":"次の手順"}</button></div><div class="small">目安 ${s.mins}分</div></div>`).join("");$("routineProgress").style.width=(routineState.index/r.steps.length*100)+"%";$("routineTimer").textContent=fmtTime(Math.floor((Date.now()-routineState.started)/1000))}
function completeRoutineStep(i){if(!routineState||i!==routineState.index)return;const r=db.routines.find(x=>String(x.id)===String(routineState.id));if(!r)return;const now=Date.now(),stepSec=Math.max(0,Math.floor((now-routineState.stepStarted)/1000)),totalSec=Number(routineState.elapsedBeforeStep||0)+stepSec;routineState.index=i+1;if(routineState.index>=r.steps.length){logSeconds(totalSec,"ルーティン",r.name);stopRoutine();toast("ルーティン完了！おつかれさま ♡");render();return}routineState.elapsedBeforeStep=totalSec;routineState.stepStarted=now;renderRunningSteps()}
function startRoutineInterval(){clearInterval(routineInterval);routineInterval=setInterval(()=>{if(routineState&&$("routineTimer"))$("routineTimer").textContent=fmtTime(Math.floor((Date.now()-routineState.started)/1000))},1000)}
function stopRoutine(){clearInterval(routineInterval);routineInterval=null;routineState=null;if($("routineRunner"))$("routineRunner").classList.add("hidden")}
function deleteRoutine(id){if(!confirm("このルーティンを削除しますか？"))return;if(routineState&&String(routineState.id)===String(id))stopRoutine();db.routines=db.routines.filter(r=>String(r.id)!==String(id));save();render()}
let activeTask=null,taskInterval=null;
function startTaskTimer(id){const t=db.tasks.find(x=>String(x.id)===String(id));if(!t)return;if(activeTask){if(!confirm("計測中のタイマーを切り替えますか？"))return;stopTaskTimer(false)}activeTask={id:t.id,name:t.name,cat:t.cat,started:Date.now()};const old=$("activeTimerCard");if(old)old.remove();const b=document.createElement("div");b.className="card";b.id="activeTimerCard";b.innerHTML=`<h2>タスク計測中</h2><div id="activeTimerName">${esc(t.name)}</div><div class="timer" id="activeTimerClock">00:00</div><button class="btn primary" onclick="stopTaskTimer(true)">計測終了・記録</button>`;$("page-tasks").insertBefore(b,$("page-tasks").firstChild);showPage("tasks");clearInterval(taskInterval);taskInterval=setInterval(updateTaskClock,1000);updateTaskClock()}
function updateTaskClock(){if(activeTask&&$("activeTimerClock"))$("activeTimerClock").textContent=fmtTime(Math.floor((Date.now()-activeTask.started)/1000))}
function stopTaskTimer(shouldSave){clearInterval(taskInterval);taskInterval=null;if(activeTask&&shouldSave){const sec=Math.floor((Date.now()-activeTask.started)/1000);logSeconds(sec,activeTask.cat,activeTask.name);toast("時間を記録しました")}activeTask=null;const el=$("activeTimerCard");if(el)el.remove();render()}
function logSeconds(sec,cat,name){if(sec<=0)return;if(!Array.isArray(db.records[dateKey()]))db.records[dateKey()]=[];db.records[dateKey()].push({sec:Math.max(0,Number(sec)||0),cat:cat||"その他",name:name||"",at:new Date().toISOString()});save()}
let focusInterval=null,focusEnd=0;
function startFocus(){stopFocus(false);focusEnd=Date.now()+5*60*1000;focusInterval=setInterval(()=>{const rem=Math.max(0,Math.ceil((focusEnd-Date.now())/1000));$("focusClock").textContent=fmtTime(rem);if(rem<=0){clearInterval(focusInterval);focusInterval=null;logSeconds(300,"集中","5分集中");toast("5分間おつかれさま！");render()}},250);toast("5分集中スタート！")}
function stopFocus(reset=true){clearInterval(focusInterval);focusInterval=null;if(reset)$("focusClock").textContent="05:00"}
let prepInterval=null,prepEnd=0;
function planPrep(){const lines=$("prepTasks").value.split("\n").map(s=>s.trim()).filter(Boolean);if(!lines.length)return toast("準備することを入力してください");const [h,m]=($("leaveTime").value||"08:00").split(":").map(Number),now=new Date(),leave=new Date();leave.setHours(h,m,0,0);if(leave<=now)leave.setDate(leave.getDate()+1);const mins=Math.max(0,Math.floor((leave-now)/60000));$("prepRemaining").textContent="出発まで "+mins+"分";const each=Math.floor(mins/lines.length),extra=mins%lines.length;$("prepPlan").innerHTML=lines.map((s,i)=>`<div class="step"><strong>${i+1}. ${esc(s)}</strong><div class="small">目安 ${each+(i<extra?1:0)}分</div></div>`).join("");$("prepResult").classList.remove("hidden");prepEnd=leave.getTime();$("prepClock").textContent=fmtTime(mins*60);toast("準備プランを作りました")}
function startPrepClock(){if(!prepEnd){planPrep();if(!prepEnd)return}clearInterval(prepInterval);const tick=()=>{const rem=Math.max(0,Math.ceil((prepEnd-Date.now())/1000));$("prepClock").textContent=fmtTime(rem);if(rem<=0){clearInterval(prepInterval);prepInterval=null;toast("出発時刻です！")}};tick();if(prepEnd>Date.now())prepInterval=setInterval(tick,250);toast("出発までのタイマーを開始しました")}
function stopPrepClock(){clearInterval(prepInterval);prepInterval=null}
function loadTodayReflection(){const r=db.reflection[dateKey()]||{};$("reflectionWin").value=r.win||"";$("reflectionBlock").value=r.block||"";$("reflectionNext").value=r.next||"";$("reflectionSaved").textContent=r.saved?"今日の振り返りは保存済み ♡":""}
function saveReflection(){db.reflection[dateKey()]={win:$("reflectionWin").value,block:$("reflectionBlock").value,next:$("reflectionNext").value,saved:true,updatedAt:new Date().toISOString()};save();$("reflectionSaved").textContent="保存しました ♡";renderReview();toast("振り返りを保存しました")}
let historyOpen=false;
function toggleReflectionHistory(){historyOpen=!historyOpen;$("reflectionHistory").classList.toggle("hidden",!historyOpen);$("historyToggle").textContent=historyOpen?"履歴を閉じる":"履歴を見る";if(historyOpen)renderReflectionHistory()}
function renderReflectionHistory(){const el=$("reflectionHistory");if(!el)return;const entries=Object.entries(db.reflection||{}).filter(([k,r])=>k!==dateKey()&&r&&r.saved).sort((a,b)=>b[0].localeCompare(a[0]));if(!entries.length){el.innerHTML='<div class="empty">まだ過去の振り返りはありません。</div>';return}el.innerHTML=entries.map(([k,r])=>`<details class="history-entry"><summary>${esc(k)}</summary><label>できたこと</label><textarea id="hist-win-${esc(k)}">${esc(r.win||"")}</textarea><label>困ったこと</label><textarea id="hist-block-${esc(k)}">${esc(r.block||"")}</textarea><label>明日やりたいこと</label><textarea id="hist-next-${esc(k)}">${esc(r.next||"")}</textarea><button class="btn primary small" onclick="updateOldReflection('${esc(k)}')">この記録を更新</button></details>`).join("")}
function updateOldReflection(k){if(!db.reflection[k])return;const a=$("hist-win-"+k),b=$("hist-block-"+k),c=$("hist-next-"+k);if(!a||!b||!c)return;db.reflection[k]={...db.reflection[k],win:a.value,block:b.value,next:c.value,updatedAt:new Date().toISOString()};save();toast("過去の記録を更新しました")}
function renderReview(){const done=todayTasks().filter(t=>t.done).length;$("reviewDone").textContent=done;$("reviewTime").textContent=minutesText(todaySeconds());if(historyOpen)renderReflectionHistory()}
function changeTheme(theme){db.theme=theme;save();applyTheme();toast("テーマを変更しました")}
function exportData(){save();const blob=new Blob([JSON.stringify(db,null,2)],{type:"application/json"}),url=URL.createObjectURL(blob),a=document.createElement("a");a.href=url;a.download="FLOW-backup-"+dateKey()+".json";document.body.appendChild(a);a.click();a.remove();setTimeout(()=>URL.revokeObjectURL(url),1000);toast("バックアップを作成しました")}
function importData(){const file=$("importFile").files[0];if(!file)return toast("バックアップファイルを選んでください");if(!confirm("現在のデータを、選択したバックアップの内容に置き換えますか？"))return;const reader=new FileReader();reader.onload=()=>{try{const parsed=JSON.parse(reader.result);if(!parsed||typeof parsed!=="object"||Array.isArray(parsed))throw Error("invalid");db=normalize(parsed);save();historyOpen=false;$("reflectionHistory").classList.add("hidden");render();loadTodayReflection();toast("バックアップを復元しました")}catch(e){toast("ファイルを読み込めませんでした。FLOWのバックアップか確認してください")}};reader.onerror=()=>toast("ファイルを読み込めませんでした");reader.readAsText(file)}
function resetApp(){if(!confirm("本当に初期化しますか？先にバックアップを取ってください。"))return;if(!confirm("タスク・目標・記録・振り返りを含めて初期化します。続けますか？"))return;stopTaskTimer(false);stopRoutine();stopFocus(false);stopPrepClock();db=fresh();save();historyOpen=false;$("reflectionHistory").classList.add("hidden");render();loadTodayReflection();showPage("home");toast("初期化しました")}
function dailyMaintenance(){if(!db.dailyTasks)db.dailyTasks={};if(!db.dailyTasks[dateKey()])db.dailyTasks[dateKey()]={}}
dailyMaintenance();save();render();loadTodayReflection();
</script>
</body>
</html>