<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#f5f0e8">
<title>FLOW ♡</title>
<style>
:root{--bg:#f7f3ed;--paper:#fffdf9;--ink:#403b38;--muted:#8c827a;--accent:#b8a5c9;--soft:#eee6f4;--line:#e9e1d8;--good:#849d85;--danger:#d93649}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:-apple-system,BlinkMacSystemFont,"Hiragino Sans","Yu Gothic",sans-serif;font-size:15px;line-height:1.65}
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
.card{background:var(--paper);border:1px solid var(--line);border-radius:18px;padding:17px;margin:13px 0;box-shadow:0 4px 18px #40352b08}
.row{display:flex;align-items:center;gap:9px}
.between{display:flex;align-items:center;justify-content:space-between;gap:10px}
.wrap{flex-wrap:wrap}
.grow{flex:1;min-width:0}
.btn{border:1px solid var(--line);border-radius:12px;padding:9px 12px;background:white;color:var(--ink)}
.btn.primary{background:var(--soft);border-color:var(--soft)}
.btn.dark{background:var(--ink);color:white}
.btn.small{font-size:12px;padding:6px 9px}
.btn.danger{color:var(--danger)}
.btn:disabled{opacity:.4;cursor:not-allowed}
input,textarea,select{width:100%;border:1px solid var(--line);border-radius:10px;padding:10px;background:white;color:var(--ink);margin:4px 0 10px}
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
.nav{position:fixed;z-index:5;bottom:0;left:0;right:0;display:flex;justify-content:flex-start;gap:3px;background:#fffdf9f5;border-top:1px solid var(--line);padding:7px 3px max(8px,env(safe-area-inset-bottom));backdrop-filter:blur(12px);overflow-x:auto}
.nav button{flex:1 0 65px;max-width:105px;min-width:65px;border:0;background:transparent;color:var(--muted);border-radius:11px;padding:7px 1px;font-size:11px}
.nav button span{display:block;font-size:19px;line-height:1.3}
.nav button.active{background:var(--soft);color:var(--ink)}
.timer{text-align:center;padding:16px 0;font-size:43px;font-weight:750;font-variant-numeric:tabular-nums}
.step{padding:10px 0;border-bottom:1px solid var(--line)}
.history-entry{background:#faf7f2;border-radius:12px;padding:12px;margin-top:10px}
hr{border:0;border-top:1px solid var(--line);margin:15px 0}
.hidden{display:none!important}
.toast{position:fixed;z-index:20;bottom:95px;left:50%;transform:translateX(-50%);background:var(--ink);color:white;padding:9px 15px;border-radius:20px;font-size:13px;display:none;max-width:90%}
.guide details{border-bottom:1px solid var(--line);padding:10px 0}
.guide summary{font-weight:700;cursor:pointer;padding:3px 0}
.guide ul{padding-left:22px}
.guide li{margin:5px 0}
.guide-note{background:#faf7f2;border-radius:12px;padding:12px;margin-top:12px}
.step-editor{display:grid;grid-template-columns:minmax(0,1fr) 78px minmax(110px,1fr);gap:6px;align-items:end;margin:9px 0}
.step-editor input,.step-editor select{min-width:0;padding:9px 6px;font-size:12px}
.step-editor .remove{grid-column:1/-1;justify-self:end}
.prep-item{padding:12px 0;border-bottom:1px solid var(--line)}
.prep-item:last-child{border-bottom:0}
.prep-item label{display:flex;align-items:flex-start;gap:8px;color:var(--ink);font-size:14px}
.prep-item input{width:19px;height:19px;margin:3px 0;accent-color:var(--accent)}
.countdown-runner{margin:0 0 14px!important;border-radius:22px!important;padding:16px!important}
.countdown-stage{display:flex;flex-direction:column;align-items:center;gap:10px;padding:8px 0}
.countdown-planned{font-size:20px;font-weight:800;letter-spacing:.03em}
.countdown-ring{--ring-color:var(--accent);--ring-progress:100%;width:min(70vw,300px);aspect-ratio:1;border-radius:50%;padding:9px;background:conic-gradient(var(--ring-color) var(--ring-progress),#e9e1d8 0);display:grid;place-items:center}
.countdown-inner{width:100%;height:100%;border-radius:50%;background:var(--paper);display:flex;flex-direction:column;justify-content:center;align-items:center;gap:7px;text-align:center}
.countdown-step{font-size:14px;font-weight:750;max-width:85%;overflow-wrap:anywhere}
.countdown-time{font-size:clamp(52px,15vw,78px);font-weight:350;letter-spacing:-.055em;line-height:1.05;font-variant-numeric:tabular-nums}
.countdown-time.over{color:#d93649}
.countdown-ring.over{--ring-color:#d93649}
.countdown-status{font-size:12px;color:var(--muted);font-weight:700}
.countdown-over{font-size:12px;color:#d93649;font-weight:800;min-height:18px}
.countdown-elapsed{width:100%;text-align:right;font-size:11px;color:var(--muted);font-variant-numeric:tabular-nums}
.countdown-controls{display:flex;gap:8px;width:100%}
.countdown-controls button{flex:1;min-height:48px}
.study-ring{--study-progress:0deg;width:min(72vw,290px);aspect-ratio:1;border-radius:50%;padding:10px;margin:15px auto;background:conic-gradient(var(--accent) var(--study-progress),var(--line) 0);display:grid;place-items:center}
.study-ring-inner{width:100%;height:100%;border-radius:50%;background:var(--paper);display:flex;flex-direction:column;align-items:center;justify-content:center}
.study-clock{font-size:clamp(48px,13vw,68px);font-weight:350;letter-spacing:-.05em;font-variant-numeric:tabular-nums;line-height:1.2}
.study-calendar{display:grid;grid-template-columns:repeat(7,1fr);gap:5px;text-align:center}
.calendar-day{min-height:57px;border-radius:10px;padding:5px 1px;background:#faf7f2;font-size:11px;display:flex;flex-direction:column;align-items:center;justify-content:center}
.calendar-day.today{outline:2px solid var(--accent)}
.calendar-day.selected{background:var(--soft)}
.calendar-day .dot{width:5px;height:5px;border-radius:50%;background:var(--accent);margin-top:3px}
.calendar-head{font-size:11px;color:var(--muted);padding:4px}
.study-bar-row{display:grid;grid-template-columns:65px 1fr 45px;gap:7px;align-items:center;margin:9px 0;font-size:12px}
.study-bar{height:8px;border-radius:9px;background:var(--line);overflow:hidden}
.study-bar span{display:block;height:100%;background:var(--accent);border-radius:9px}
.material-item{padding:10px 0;border-bottom:1px solid var(--line)}
.share-preview{width:min(100%,360px);aspect-ratio:1;border-radius:50%;margin:12px auto;background:var(--soft);display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:32px;overflow:hidden;border:8px solid var(--paper);outline:1px solid var(--line)}
.share-preview .share-brand{font-size:11px;letter-spacing:3px}
.share-preview .share-time{font-size:clamp(38px,10vw,54px);font-weight:750;line-height:1.2;margin:12px 0}
.share-preview .share-date{font-size:13px}
.share-preview .share-comment{font-size:13px;max-width:90%;overflow-wrap:anywhere;margin-top:12px}
#scanVideo{width:100%;border-radius:14px;background:#222;max-height:280px;object-fit:cover}
@media(max-width:390px){.nav{gap:0}.nav button{font-size:10px}.nav button span{font-size:17px}.btn{padding:8px 10px}.step-editor{grid-template-columns:minmax(0,1fr) 65px 105px;gap:4px}}
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
  <div class="between"><div><div class="small">今日の達成率</div><div class="big" id="homePercent">0%</div></div><div style="text-align:right"><div class="small">今日のタスク</div><strong id="homeCount">0 / 0</strong></div></div>
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
 <div class="card"><div class="between"><h2>今日のタスク</h2><span class="pill" id="taskCounter">0件</span></div><p class="small">チェックは日付ごとに保存されます。</p><div id="taskList"></div></div>
 <div class="card"><h2>タスクを追加</h2><label for="taskName">やること</label><input id="taskName" placeholder="例：英単語を覚える">
  <div class="grid2"><div><label for="taskMins">予定時間（分）</label><input id="taskMins" type="number" min="1" value="15"></div><div><label for="taskCat">カテゴリー</label><select id="taskCat"><option>勉強</option><option>学校</option><option>生活</option><option>運動</option><option>美容</option><option>その他</option></select></div></div>
  <label for="taskGoal">関連する目標</label><select id="taskGoal"></select><button class="btn primary" onclick="addTask()">＋ タスクを追加</button>
 </div>
 <div class="card hidden" id="activeTimerCard"><h2>タスク計測中</h2><div id="activeTimerName"></div><div class="timer" id="activeTimerClock">00:00</div><button class="btn primary" onclick="stopTaskTimer(true)">計測終了・記録</button></div>
</section>

<section class="page" id="page-goals">
 <div class="card"><h2>わたしの目標</h2><p class="small">目標を毎日の行動につなげよう。</p><div id="goalList"></div></div>
 <div class="card"><h2>新しい目標</h2><label for="goalName">目標</label><input id="goalName" placeholder="例：看護学校に合格する"><label for="goalWhy">達成したい理由（任意）</label><textarea id="goalWhy" placeholder="どんな自分になりたい？"></textarea><button class="btn primary" onclick="addGoal()">＋ 目標を追加</button></div>
</section>

<section class="page" id="page-routines">
 <div class="card countdown-runner hidden" id="routineRunner">
  <div class="between"><h2 id="runningTitle">ルーティン実行中</h2><span class="pill" id="routineStepCount"></span></div>
  <div class="countdown-stage"><div class="countdown-planned" id="routinePlanned">設定時間 --:--</div><div class="countdown-ring" id="routineRing"><div class="countdown-inner"><div class="countdown-step" id="routineStepName">準備中</div><div class="countdown-time" id="routineTimer">00:00</div><div class="countdown-status" id="routineStatus">残り時間</div><div class="countdown-over" id="routineOver"></div></div></div>
  <div class="countdown-elapsed" id="routineElapsed">実際にかかった時間 00:00</div><div class="progress" style="width:100%"><span id="routineProgress" style="width:0%"></span></div>
  <div class="countdown-controls"><button class="btn" onclick="pauseRoutine()" id="routinePauseBtn">一時停止</button><button class="btn primary" onclick="completeRoutineStep()">次の項目へ</button><button class="btn danger" onclick="stopRoutine()">終了</button></div></div><div id="runningSteps"></div>
 </div>
 <div class="card"><h2>わたしのルーティン</h2><p class="small">各ステップの時間を自分で設定できます。最大3つです。</p><div id="routineList"></div></div>
 <div class="card"><h2 id="routineFormTitle">ルーティンを作る</h2><label for="routineName">ルーティン名</label><input id="routineName" placeholder="例：学校に行く準備"><div class="between"><h3>ステップ</h3><button class="btn small" onclick="addRoutineStepRow()">＋ ステップ追加</button></div><div class="small">時間は自分で入力してください。自動で割り当てません。</div><div id="routineStepEditor"></div><hr><div class="between"><span class="small">合計所要時間</span><strong id="routineTotal">0分</strong></div><div class="row wrap" style="margin-top:12px"><button class="btn primary" onclick="saveRoutine()">保存する</button><button class="btn" onclick="cancelRoutineEdit()">キャンセル</button></div></div>
</section>

<section class="page" id="page-prep">
 <div class="card countdown-runner hidden" id="prepRunnerCard">
  <div class="between"><h2>お出かけ準備タイマー</h2><span class="pill" id="prepStepCount"></span></div><div class="countdown-stage"><div class="countdown-planned" id="prepPlanned">設定時間 --:--</div><div class="countdown-ring" id="prepRing"><div class="countdown-inner"><div class="countdown-step" id="prepCurrentStep">準備中</div><div class="countdown-time" id="prepClock">00:00</div><div class="countdown-status" id="prepStatus">残り時間</div><div class="countdown-over" id="prepOver"></div></div></div><div class="countdown-elapsed" id="prepElapsed">実際にかかった時間 00:00</div><div class="progress" style="width:100%"><span id="prepProgress" style="width:0%"></span></div><div class="countdown-controls"><button class="btn" onclick="pausePrepClock()" id="prepPauseBtn">一時停止</button><button class="btn primary" onclick="nextPrepStep()">次の項目へ</button><button class="btn danger" onclick="stopPrepClock()">終了</button></div></div>
 </div>
 <div class="card"><h2>お出かけ準備</h2><p class="small">出発時間に合わせて、今できる準備を整理します。</p><label for="leaveTime">出発時刻</label><input type="time" id="leaveTime" value="08:00"><label for="prepRoutineSelect">登録済みルーティン</label><select id="prepRoutineSelect"><option value="">ルーティンを選んでください</option></select><button class="btn" onclick="appendSelectedRoutineToPrep()">＋ ルーティンを追加</button><hr><h3>今回の準備項目</h3><p class="small">今回だけ省略したい項目は、チェックを外せます。</p><div id="prepItems"></div><div class="row wrap"><button class="btn" onclick="addPrepItem()">＋ 項目を追加</button><button class="btn primary" onclick="planPrep()">準備プランを作る</button></div><div class="stat" style="margin-top:14px"><div class="small">出発まで</div><div class="big" id="prepRemaining">--分</div></div></div>
 <div class="card hidden" id="prepResult"><h2>今回の準備プラン</h2><div class="stat" id="prepMessage"></div><div id="prepPlan"></div><hr><div class="between"><span class="small">選択した準備の合計</span><strong id="prepTotal">0分</strong></div><div class="small" id="prepDifference"></div><button class="btn primary" style="margin-top:12px" onclick="acceptPrepPlan()">この提案で準備を開始</button></div>
 <div class="card"><h2>5分だけ集中</h2><p class="small">まずは5分だけ始めてみましょう。</p><div class="timer" id="focusClock">05:00</div><button class="btn primary" onclick="startFocus()">スタート</button><button class="btn" onclick="stopFocus()">停止・リセット</button></div>
</section><section class="page" id="page-study">
 <div class="card">
  <div class="between"><h2>勉強タイマー</h2><span class="pill" id="studyTimerStatus">待機中</span></div>
  <div class="study-ring" id="studyRing"><div class="study-ring-inner"><div class="small">STUDY TIME</div><div class="study-clock" id="studyClock">00:00:00</div><div class="small" id="studyClockHint">今日の積み重ね</div></div></div>
  <label for="studySubject">科目</label><select id="studySubject"><option>英語</option><option>数学IA</option><option>数学IIBC</option><option>国語</option><option>日本史</option><option>政治経済</option><option>理科</option><option>その他</option></select>
  <label for="studyMaterial">教材</label><select id="studyMaterial"><option value="">教材を選択（任意）</option></select>
  <div class="grid2"><div><label for="studyGoal">関連する目標</label><select id="studyGoal"><option value="">選択なし</option></select></div><div><label for="studyTask">関連タスク</label><select id="studyTask"><option value="">選択なし</option></select></div></div>
  <div class="row"><button class="btn primary grow" id="studyStartBtn" onclick="startStudyTimer()">勉強スタート</button><button class="btn grow" id="studyPauseBtn" onclick="pauseStudyTimer()" disabled>一時停止</button></div>
  <button class="btn danger" style="width:100%;margin-top:8px" id="studyFinishBtn" onclick="finishStudyTimer()" disabled>終了して記録</button>
  <p class="small">カウントアップ式。停止中の時間は記録されません。</p>
 </div>

 <!-- 手動記録追加 -->
 <div class="card">
  <h2>手動で勉強記録を追加</h2>
  <p class="small">タイマーを使わなかった日も、あとから記録できます。</p>
  <label for="manualStudyDate">勉強した日</label>
  <input type="date" id="manualStudyDate">
  <label for="manualStudySubject">科目</label>
  <select id="manualStudySubject"><option>英語</option><option>数学IA</option><option>数学IIBC</option><option>国語</option><option>日本史</option><option>政治経済</option><option>理科</option><option>その他</option></select>
  <div class="grid2">
   <div><label for="manualStudyHours">時間</label><input type="number" id="manualStudyHours" min="0" max="24" value="0" inputmode="numeric"></div>
   <div><label for="manualStudyMinutes">分</label><input type="number" id="manualStudyMinutes" min="0" max="59" value="30" inputmode="numeric"></div>
  </div>
  <label for="manualStudyMaterial">教材（任意）</label>
  <select id="manualStudyMaterial"><option value="">選択なし</option></select>
  <div class="grid2">
   <div><label for="manualStudyGoal">関連する目標（任意）</label><select id="manualStudyGoal"><option value="">選択なし</option></select></div>
   <div><label for="manualStudyTask">関連タスク（任意）</label><select id="manualStudyTask"><option value="">選択なし</option></select></div>
  </div>
  <button class="btn primary" style="width:100%" onclick="addManualStudyRecord()">＋ 勉強記録を追加</button>
 </div>

 <div class="grid2">
  <div class="stat"><div class="small">今週の勉強時間</div><div class="big" id="studyWeekTotal">0分</div></div>
  <div class="stat"><div class="small">今月の勉強時間</div><div class="big" id="studyMonthTotal">0分</div></div>
 </div>
 <div class="card"><div class="between"><h2>科目別の記録</h2><span class="small">今月</span></div><div id="studySubjectStats"></div></div>
 <div class="card">
  <div class="between"><h2>勉強カレンダー</h2><div class="row"><button class="btn small" onclick="changeStudyMonth(-1)">‹</button><strong id="studyMonthLabel"></strong><button class="btn small" onclick="changeStudyMonth(1)">›</button></div></div>
  <div class="study-calendar" id="studyCalendar"></div><div class="small" id="studySelectedDay"></div><div id="studyDaySessions"></div>
 </div>
 <div class="card"><div class="between"><h2>教材</h2><button class="btn small" onclick="toggleMaterialForm()">＋ 登録</button></div><div id="materialList"></div>
  <div id="materialForm" class="hidden"><hr><h3>教材を登録</h3><label for="materialISBN">ISBN（任意）</label><input id="materialISBN" inputmode="numeric" placeholder="978..."><button class="btn small" onclick="startISBNScan()">バーコードを読み取る</button><div id="scanArea" class="hidden"><video id="scanVideo" autoplay playsinline></video><p class="small" id="scanMessage"></p><button class="btn small danger" onclick="stopISBNScan()">カメラを閉じる</button></div><label for="materialTitle">教材名</label><input id="materialTitle" placeholder="例：共通テスト英語問題集"><label for="materialSubject">科目</label><select id="materialSubject"><option>英語</option><option>数学IA</option><option>数学IIBC</option><option>国語</option><option>日本史</option><option>政治経済</option><option>理科</option><option>その他</option></select><button class="btn primary" onclick="addStudyMaterial()">教材を保存</button></div>
 </div>
 <div class="card"><h2>勉強記録をシェア</h2><p class="small">今日の勉強時間を丸いカードにできます。コメントは任意です。</p><label for="shareComment">コメント（書かなくてもOK）</label><input id="shareComment" placeholder="任意"><label for="shareTheme">カードの色</label><select id="shareTheme" onchange="renderShareCard()"><option value="beige">ミルクベージュ</option><option value="lavender">ラベンダー</option><option value="mono">モノトーン</option></select><div class="share-preview" id="studyShareCard"><div class="share-brand">MY STUDY LOG</div><div class="share-date" id="shareDate"></div><div class="share-time" id="shareTime">00分</div><div class="share-date">A LITTLE PROGRESS EVERY DAY</div><div class="share-comment" id="shareCommentPreview"></div></div><button class="btn primary" style="width:100%" onclick="saveStudyShareCard()">画像を保存</button></div>
</section>

<section class="page" id="page-review">
 <div class="card"><h2>今日の振り返り</h2><p class="small">できたことも、うまくいかなかったことも、次に活かすための記録です。</p><label for="reflectionWin">今日できたこと・頑張ったこと</label><textarea id="reflectionWin" placeholder="小さなことでも大丈夫です"></textarea><label for="reflectionBlock">困ったこと・改善したいこと</label><textarea id="reflectionBlock" placeholder="次に工夫できそうなことは？"></textarea><label for="reflectionNext">明日やりたいこと</label><textarea id="reflectionNext" placeholder="明日の自分へのメモ"></textarea><button class="btn primary" onclick="saveReflection()">今日の振り返りを保存</button><p class="small" id="reflectionSaved"></p></div>
 <div class="card"><div class="between"><h2>過去の振り返り</h2><button class="btn small" id="historyToggle" onclick="toggleReflectionHistory()">履歴を見る</button></div><p class="small">読み返したいときだけ開けます。</p><div id="reflectionHistory" class="hidden"></div></div>
 <div class="card"><h2>今日の記録</h2><div class="grid2"><div class="stat"><div class="small">完了したタスク</div><div class="big" id="reviewDone">0</div></div><div class="stat"><div class="small">集中した時間</div><div class="big" id="reviewTime">0分</div></div></div></div>
</section>

<section class="page" id="page-settings">
 <div class="card"><h2>FLOWの設定</h2><label for="themeChoice">テーマ</label><select id="themeChoice" onchange="changeTheme(this.value)"><option value="beige">ミルクベージュ</option><option value="lavender">ラベンダー × 白</option><option value="mono">モノトーン</option></select></div>
 <div class="card"><h2>使い方・ガイド</h2><button class="btn primary" onclick="showPage('guide')">使い方・ガイドを読む →</button></div>
 <div class="card"><h2>データのバックアップ</h2><p class="small">タスク・目標・ルーティン・勉強記録・教材・振り返りをJSONファイルに保存します。</p><button class="btn primary" onclick="exportData()">バックアップを書き出す</button><hr><label for="importFile">バックアップファイルから復元</label><input type="file" id="importFile" accept=".json,application/json"><button class="btn" onclick="importData()">バックアップを復元</button></div>
 <div class="card"><h2>保存について</h2><p class="small">データはこのブラウザ内に保存されます。定期的にバックアップしてください。</p><button class="btn danger" onclick="resetApp()">アプリのデータを初期化</button></div>
</section>

<section class="page" id="page-guide">
 <div class="card"><div class="between"><h2>使い方・ガイド</h2><button class="btn small" onclick="showPage('settings')">← 戻る</button></div><div class="guide">
  <details open><summary>1. FLOWでできること</summary><p>目標を日々のタスクにつなげ、ルーティンや準備時間を整理し、勉強時間や振り返りを記録するアプリです。</p></details>
  <details><summary>2. タスク・目標</summary><p>タスク、目標、関連づけを登録できます。タスクのチェックは日付ごとに保存されます。</p></details>
  <details><summary>3. ルーティン</summary><p>最大3つまで登録できます。各ステップの時間は自分で入力します。</p></details>
  <details><summary>4. お出かけ準備</summary><p>出発時刻に合わせて準備項目を整理できます。元のルーティンは変更されません。</p></details>
  <details><summary>5. 勉強記録</summary><p>タイマーでも手動でも勉強時間を記録できます。教材・科目・目標・タスクを関連づけられます。月間カレンダーや科目別の時間も確認できます。</p></details>
  <details><summary>6. 教材とISBN</summary><p>教材名と科目を登録できます。バーコード読み取りはiPhoneのブラウザ環境によって利用できない場合があります。その場合はISBNを手入力してください。ISBNから書名を自動取得する機能はありません。</p></details>
  <details><summary>7. バックアップ</summary><p>設定からJSON形式で保存できます。復元すると現在のデータが選択したバックアップの内容に置き換わります。</p></details>
 </div><div class="guide-note"><strong>大切なお知らせ</strong><p>予定どおりに進まない日があっても大丈夫。必要に応じて調整し、自分のペースで使ってください。</p></div></div>
</section>

</div>
<nav class="nav">
 <button class="active" data-page="home" onclick="showPage('home')"><span>⌂</span>ホーム</button>
 <button data-page="tasks" onclick="showPage('tasks')"><span>☑</span>タスク</button>
 <button data-page="goals" onclick="showPage('goals')"><span>☆</span>目標</button>
 <button data-page="routines" onclick="showPage('routines')"><span>↻</span>ルーティン</button>
 <button data-page="prep" onclick="showPage('prep')"><span>◷</span>準備</button>
 <button data-page="study" onclick="showPage('study')"><span>◉</span>勉強</button>
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
  version:4,theme:"beige",
  goals:[
   {id:uid(),name:"看護学校に合格する",why:"自分の目標に向かって進む",done:false},
   {id:uid(),name:"体力をつける",why:"毎日を元気に過ごす",done:false},
   {id:uid(),name:"毎日英単語を覚える",why:"少しずつ積み重ねる",done:false}
  ],
  tasks:[],routines:[],records:{},reflection:{},dailyTasks:{},
  studySessions:[],materials:[]
 };
}
function normalize(x){
 const f=fresh();x=x&&typeof x==="object"?x:{};
 const tasks=Array.isArray(x.tasks)?x.tasks.map((t,i)=>({
  ...t,id:t.id||uid(),name:t.name||"やること",cat:t.cat||"その他",
  mins:Math.max(1,Number(t.mins??t.estimate??15)||15),
  goalId:t.goalId||"",done:!!t.done,order:Number(t.order??i)
 })):[];
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
   return {id:old.id||uid(),name:old.name||"ステップ",mins:Number.isFinite(mins)&&mins>0?mins:null,priority:["must","prefer","optional"].includes(old.priority)?old.priority:"prefer"};
  })
 }));
 const goals=Array.isArray(x.goals)?x.goals:f.goals;
 return {...f,...x,version:4,tasks,goals:goals.map(g=>({...g,id:g.id||uid()})),routines,dailyTasks,
  records:x.records&&typeof x.records==="object"?x.records:{},
  reflection:x.reflection&&typeof x.reflection==="object"?x.reflection:{},
  studySessions:Array.isArray(x.studySessions)?x.studySessions:[],
  materials:Array.isArray(x.materials)?x.materials:[],theme:x.theme||"beige"};
}
function loadDB(){
 try{let raw=localStorage.getItem(STORE);if(!raw)raw=localStorage.getItem(LEGACY);if(raw)return normalize(JSON.parse(raw))}
 catch(e){console.warn("FLOW data could not be read",e)}
 return fresh();
}
let db=loadDB();
function save(){try{localStorage.setItem(STORE,JSON.stringify(db))}catch(e){toast("保存できませんでした。バックアップを確認してください。")}}
function toast(msg){const el=$("toast");el.textContent=msg;el.style.display="block";clearTimeout(toast.timer);toast.timer=setTimeout(()=>el.style.display="none",2400)}
function taskDone(id,k=dateKey()){return !!db.dailyTasks?.[k]?.[String(id)]}
function setTaskDone(id,value,k=dateKey()){if(!db.dailyTasks)db.dailyTasks={};if(!db.dailyTasks[k])db.dailyTasks[k]={};db.dailyTasks[k][String(id)]=!!value;save()}
function todayTasks(){return db.tasks.map(t=>({...t,done:taskDone(t.id)}))}
function todaySeconds(){return (db.records[dateKey()]||[]).reduce((a,r)=>a+Number(r.sec||0),0)}
function fmtTime(sec){sec=Math.max(0,Math.floor(sec));return String(Math.floor(sec/60)).padStart(2,"0")+":"+String(sec%60).padStart(2,"0")}
function fmtStudyTime(sec){sec=Math.max(0,Math.floor(sec));const h=Math.floor(sec/3600),m=Math.floor(sec%3600/60),s=sec%60;return [h,m,s].map(n=>String(n).padStart(2,"0")).join(":")}
function minutesText(sec){const n=Math.round(sec/60);return n<60?n+"分":Math.floor(n/60)+"時間"+(n%60?n%60+"分":"")}
function showPage(name){
 document.querySelectorAll(".page").forEach(p=>p.classList.toggle("active",p.id==="page-"+name));
 document.querySelectorAll(".nav button").forEach(b=>b.classList.toggle("active",b.dataset.page===name));
 if(name==="review")loadTodayReflection();if(name==="study")renderStudy();render();window.scrollTo({top:0,behavior:"smooth"});
}
function applyTheme(){
 const themes={beige:["#f7f3ed","#fffdf9","#403b38","#8c827a","#b8a5c9","#eee6f4","#e9e1d8"],lavender:["#f5f1fa","#fffefe","#393440","#898092","#b8a2d5","#eee5f8","#e8dfef"],mono:["#f1f1f1","#ffffff","#292929","#777777","#777777","#e7e7e7","#dddddd"]};
 const t=themes[db.theme]||themes.beige;["--bg","--paper","--ink","--muted","--accent","--soft","--line"].forEach((k,i)=>document.documentElement.style.setProperty(k,t[i]));
 if($("themeChoice"))$("themeChoice").value=db.theme;
}
function render(){
 applyTheme();$("todayLabel").textContent=new Date().toLocaleDateString("ja-JP",{year:"numeric",month:"long",day:"numeric",weekday:"long"});
 renderHome();renderTasks();renderGoals();renderRoutines();renderPrepRoutineOptions();renderReview();
 if($("page-study").classList.contains("active"))renderStudy();
}
function renderHome(){
 const ts=todayTasks(),done=ts.filter(t=>t.done).length,total=ts.length,pct=total?Math.round(done/total*100):0;
 $("homePercent").textContent=pct+"%";$("homeCount").textContent=done+" / "+total;$("homeProgress").style.width=pct+"%";$("remaining").textContent=total-done;
 $("todayTime").textContent=minutesText(todaySeconds());$("homeMessage").textContent=total&&done===total?"今日もよく頑張りました！ ♡":done?"いい感じ！少しずつ進んでいます。":"小さな一歩から始めましょう。";
 $("homeTasks").innerHTML=ts.length?ts.slice(0,5).map(taskHTML).join(""):'<div class="empty">タスクを追加してみましょう ♡</div>';
 $("homeGoals").innerHTML=db.goals.length?db.goals.filter(g=>!g.done).slice(0,3).map(g=>`<div class="step">☆ ${esc(g.name)}</div>`).join(""):'<div class="empty">目標を追加してみましょう</div>';
}
function taskHTML(t){return `<div class="task ${t.done?"done":""}"><input type="checkbox" ${t.done?"checked":""} onchange="toggleTask('${esc(t.id)}',this.checked)"><div class="grow"><div class="task-name">${esc(t.name)}</div><div class="small">${esc(t.cat)} ・ ${Number(t.mins)||0}分</div></div><button class="btn small" onclick="startTaskTimer('${esc(t.id)}')">計測</button><button class="btn small danger" onclick="deleteTask('${esc(t.id)}')">削除</button></div>`}
function renderTasks(){
 const ts=todayTasks().sort((a,b)=>a.order-b.order);$("taskCounter").textContent=ts.filter(t=>t.done).length+"/"+ts.length+"件";
 $("taskList").innerHTML=ts.length?ts.map(taskHTML).join(""):'<div class="empty">まだタスクがありません。下から追加してください。</div>';
 $("taskGoal").innerHTML='<option value="">目標と関連づけない</option>'+db.goals.map(g=>`<option value="${esc(g.id)}">${esc(g.name)}</option>`).join("");
}
function toggleTask(id,checked){setTaskDone(id,checked);render();toast(checked?"タスク完了！おつかれさま ♡":"チェックを戻しました")}
function addTask(){const name=$("taskName").value.trim();if(!name)return toast("タスク名を入力してください");db.tasks.push({id:uid(),name,cat:$("taskCat").value,mins:Math.max(1,Number($("taskMins").value)||15),goalId:$("taskGoal").value,order:db.tasks.length});$("taskName").value="";save();render();toast("タスクを追加しました")}
function deleteTask(id){if(!confirm("このタスクを削除しますか？"))return;db.tasks=db.tasks.filter(t=>String(t.id)!==String(id));save();render()}
function addGoal(){const name=$("goalName").value.trim();if(!name)return toast("目標を入力してください");db.goals.push({id:uid(),name,why:$("goalWhy").value.trim(),done:false});$("goalName").value="";$("goalWhy").value="";save();render();toast("目標を追加しました")}
function renderGoals(){
 $("goalList").innerHTML=db.goals.length?db.goals.map(g=>{const related=db.tasks.filter(t=>String(t.goalId)===String(g.id));return `<div class="step"><div class="between"><strong>${esc(g.name)}</strong><button class="btn small" onclick="toggleGoal('${esc(g.id)}')">${g.done?"達成済み ✓":"達成にする"}</button></div>${g.why?`<div class="small">${esc(g.why)}</div>`:""}<div class="small">関連タスク：${related.length}件</div>${related.map(t=>`<div class="small">・${esc(t.name)}${taskDone(t.id)?" ✓":""}</div>`).join("")}<button class="btn small danger" style="margin-top:7px" onclick="deleteGoal('${esc(g.id)}')">削除</button></div>`}).join(""):'<div class="empty">目標を追加してみましょう。</div>';
}
function toggleGoal(id){const g=db.goals.find(x=>String(x.id)===String(id));if(g)g.done=!g.done;save();render()}
function deleteGoal(id){if(!confirm("この目標を削除しますか？"))return;db.goals=db.goals.filter(g=>String(g.id)!==String(id));save();render()}
let editingRoutineId=null;
function addRoutineStepRow(step={}){
 const editor=$("routineStepEditor"),row=document.createElement("div");row.className="step-editor";
 const name=document.createElement("input");name.className="routine-step-name";name.placeholder="ステップ名";name.value=step.name||"";
 const mins=document.createElement("input");mins.className="routine-step-mins";mins.type="number";mins.min="1";mins.step="1";mins.placeholder="分";mins.value=step.mins??"";
 const priority=document.createElement("select");priority.className="routine-step-priority";
 [["must","必須"],["prefer","できればやる"],["optional","省略可能"]].forEach(([v,l])=>{const o=document.createElement("option");o.value=v;o.textContent=l;priority.appendChild(o)});
 priority.value=step.priority||"prefer";
 const remove=document.createElement("button");remove.type="button";remove.className="btn small danger remove";remove.textContent="このステップを削除";remove.onclick=()=>{row.remove();updateRoutineTotal()};
 [name,mins,priority].forEach(el=>el.addEventListener("input",updateRoutineTotal));
 row.append(name,mins,priority,remove);editor.appendChild(row);updateRoutineTotal();
}
function readRoutineEditor(){
 return [...document.querySelectorAll("#routineStepEditor .step-editor")].map(row=>({id:row.dataset.id||uid(),name:row.querySelector(".routine-step-name").value.trim(),mins:row.querySelector(".routine-step-mins").value===""?null:Number(row.querySelector(".routine-step-mins").value),priority:row.querySelector(".routine-step-priority").value})).filter(s=>s.name);
}
function updateRoutineTotal(){
 const rows=[...document.querySelectorAll("#routineStepEditor .step-editor")];let total=0,missing=0;
 rows.forEach(row=>{const v=row.querySelector(".routine-step-mins").value;if(v===""||!Number.isFinite(Number(v))||Number(v)<=0)missing++;else total+=Number(v)});
 $("routineTotal").textContent=total+"分"+(missing?"（時間未入力 "+missing+"件）":"");
}
function createRoutine(){
 if(db.routines.length>=3)return toast("ルーティンは最大3つまでです");
 editingRoutineId=null;$("routineFormTitle").textContent="ルーティンを作る";$("routineName").value="";$("routineStepEditor").innerHTML="";addRoutineStepRow();$("routineName").scrollIntoView({behavior:"smooth",block:"center"});
}
function editRoutine(id){
 const r=db.routines.find(x=>String(x.id)===String(id));if(!r)return;
 editingRoutineId=r.id;$("routineFormTitle").textContent="ルーティンを編集";$("routineName").value=r.name;$("routineStepEditor").innerHTML="";
 r.steps.forEach(s=>{const n=$("routineStepEditor").children.length;addRoutineStepRow(s);$("routineStepEditor").children[n].dataset.id=s.id});
 $("routineName").scrollIntoView({behavior:"smooth",block:"center"});
}
function cancelRoutineEdit(){editingRoutineId=null;$("routineName").value="";$("routineStepEditor").innerHTML="";$("routineFormTitle").textContent="ルーティンを作る";updateRoutineTotal()}
function saveRoutine(){
 const name=$("routineName").value.trim(),steps=readRoutineEditor();
 if(!name)return toast("ルーティン名を入力してください");if(!steps.length)return toast("ステップを1つ以上追加してください");
 if(steps.some(s=>!Number.isFinite(s.mins)||s.mins<=0))return toast("各ステップの時間を1分以上で入力してください");
 const clean=steps.map(s=>({...s,mins:Math.round(s.mins)}));
 if(editingRoutineId){const r=db.routines.find(x=>String(x.id)===String(editingRoutineId));if(!r)return toast("ルーティンが見つかりません");r.name=name;r.steps=clean;toast("ルーティンを更新しました")}
 else{if(db.routines.length>=3)return toast("ルーティンは最大3つまでです");db.routines.push({id:uid(),name,steps:clean});toast("ルーティンを保存しました")}
 cancelRoutineEdit();save();render();
}
function routineTotal(r){return r.steps.reduce((sum,s)=>sum+(Number(s.mins)||0),0)}
function renderRoutines(){
 $("routineList").innerHTML=db.routines.length?db.routines.map(r=>`<div class="step"><div class="between"><strong>${esc(r.name)}</strong><span class="pill">${routineTotal(r)}分</span></div>${r.steps.map((s,i)=>`<div class="step"><div class="between"><span>${i+1}. ${esc(s.name)}</span><strong>${s.mins??"未設定"}分</strong></div><span class="pill ${s.priority}">${priorityLabels[s.priority]||"できればやる"}</span></div>`).join("")}<div class="row wrap" style="margin-top:10px"><button class="btn primary small" onclick="startRoutine('${esc(r.id)}')">開始</button><button class="btn small" onclick="editRoutine('${esc(r.id)}')">編集</button><button class="btn small danger" onclick="deleteRoutine('${esc(r.id)}')">削除</button></div></div>`).join(""):'<div class="empty">ルーティンを作ってみましょう。</div>';
 if(routineState)renderRunningSteps();
}
function deleteRoutine(id){if(!confirm("このルーティンを削除しますか？"))return;if(routineState&&String(routineState.id)===String(id))stopRoutine();db.routines=db.routines.filter(r=>String(r.id)!==String(id));save();render()}

let routineState=null,routineInterval=null;
function startRoutine(id){
 const r=db.routines.find(x=>String(x.id)===String(id));if(!r||!r.steps.length)return;
 if(r.steps.some(x=>!Number(x.mins)||Number(x.mins)<=0))return toast("時間が未入力のステップがあります。編集してください。");
 stopRoutine();routineState={id:r.id,index:0,stepStarted:Date.now(),elapsedBeforeStep:0,paused:false,totalElapsed:0};
 $("routineRunner").classList.remove("hidden");showPage("routines");$("routineRunner").classList.remove("hidden");renderRunningSteps();startRoutineInterval();updateRoutineTimer();$("routineRunner").scrollIntoView({behavior:"smooth",block:"start"});
}
function currentRoutine(){return routineState?db.routines.find(r=>String(r.id)===String(routineState.id)):null}
function routineElapsed(){if(!routineState)return 0;return routineState.elapsedBeforeStep+(routineState.paused?0:Date.now()-routineState.stepStarted)}
function renderRunningSteps(){
 if(!routineState)return;const r=currentRoutine();if(!r)return;const step=r.steps[routineState.index];if(!step)return;
 $("runningTitle").textContent=r.name;$("routineStepCount").textContent=(routineState.index+1)+"/"+r.steps.length;$("routineStepName").textContent=step.name;$("routinePlanned").textContent="設定時間 "+fmtTime(Number(step.mins)*60);
 $("routineProgress").style.width=(routineState.index/r.steps.length*100)+"%";$("routinePauseBtn").textContent=routineState.paused?"再開":"一時停止";
 $("runningSteps").innerHTML=r.steps.map((x,i)=>`<div class="step"><div class="between"><span>${i+1}. ${esc(x.name)}</span><span class="small">${x.mins}分</span></div><div class="small">${i===routineState.index?"実行中":i<routineState.index?"完了":"これから"}</div></div>`).join("");updateRoutineTimer();
}
function updateRoutineTimer(){
 if(!routineState)return;const r=currentRoutine();if(!r)return;const step=r.steps[routineState.index];if(!step)return;
 const elapsed=routineElapsed()/1000,planned=Number(step.mins)*60,remain=Math.ceil(planned-elapsed),over=remain<0;
 $("routineTimer").textContent=over?"+"+fmtTime(-remain):fmtTime(remain);$("routineTimer").classList.toggle("over",over);$("routineRing").classList.toggle("over",over);
 $("routineRing").style.setProperty("--ring-progress",(Math.max(0,Math.min(1,(planned-elapsed)/planned))*100)+"%");
 $("routineStatus").textContent=over?"予定時間を超過":"残り時間";$("routineOver").textContent=over?"予定より "+fmtTime(-remain)+" 超過":"";$("routineElapsed").textContent="実際にかかった時間 "+fmtTime(Math.floor(elapsed));
}
function completeRoutineStep(){
 if(!routineState)return;const r=currentRoutine();if(!r)return;const sec=Math.floor(routineElapsed()/1000);routineState.totalElapsed+=sec;routineState.index++;
 if(routineState.index>=r.steps.length){logSeconds(routineState.totalElapsed,"ルーティン",r.name);stopRoutine();toast("ルーティン完了！おつかれさま ♡");render();return}
 routineState.elapsedBeforeStep=0;routineState.stepStarted=Date.now();routineState.paused=false;renderRunningSteps();updateRoutineTimer();
}
function pauseRoutine(){
 if(!routineState)return;if(!routineState.paused){routineState.elapsedBeforeStep=routineElapsed();routineState.paused=true}else{routineState.stepStarted=Date.now();routineState.paused=false}renderRunningSteps();
}
function startRoutineInterval(){clearInterval(routineInterval);routineInterval=setInterval(()=>{if(routineState)updateRoutineTimer()},250)}
function stopRoutine(){clearInterval(routineInterval);routineInterval=null;routineState=null;$("routineRunner").classList.add("hidden")}

/* お出かけ準備 */
let prepItems=[],prepPlan=[],prepEnd=0,prepInterval=null,prepRun=null;
function renderPrepRoutineOptions(){
 const select=$("prepRoutineSelect"),prev=select.value;select.innerHTML='<option value="">ルーティンを選んでください</option>';
 db.routines.forEach(r=>{const o=document.createElement("option");o.value=r.id;o.textContent=r.name;select.appendChild(o)});
 if(db.routines.some(r=>String(r.id)===String(prev)))select.value=prev;
}
function appendSelectedRoutineToPrep(){
 const r=db.routines.find(x=>String(x.id)===String($("prepRoutineSelect").value));if(!r)return toast("ルーティンを選んでください");
 const existing=new Set(prepItems.map(x=>x.name));const add=r.steps.filter(x=>!existing.has(x.name)).map(x=>({id:uid(),name:x.name,mins:x.mins,priority:x.priority,include:true}));
 if(!add.length)return toast("この項目は追加済みです");prepItems.push(...add);renderPrepItems();toast("準備項目を追加しました");
}
function addPrepItem(){prepItems.push({id:uid(),name:"",mins:null,priority:"prefer",include:true});renderPrepItems()}
function renderPrepItems(){
 $("prepItems").innerHTML=prepItems.length?prepItems.map((x,i)=>`<div class="step"><label>項目名</label><input value="${esc(x.name)}" placeholder="準備すること" oninput="updatePrepItem(${i},'name',this.value)"><div class="grid2"><div><label>所要時間（分）</label><input type="number" min="1" value="${x.mins??""}" placeholder="分" oninput="updatePrepItem(${i},'mins',this.value)"></div><div><label>優先度</label><select onchange="updatePrepItem(${i},'priority',this.value)"><option value="must" ${x.priority==="must"?"selected":""}>必須</option><option value="prefer" ${x.priority==="prefer"?"selected":""}>できればやる</option><option value="optional" ${x.priority==="optional"?"selected":""}>省略可能</option></select></div></div><button class="btn small danger" onclick="removePrepItem(${i})">この項目を削除</button></div>`).join(""):'<div class="empty">準備項目を追加してください。</div>';
}
function updatePrepItem(i,k,v){if(!prepItems[i])return;prepItems[i][k]=k==="mins"?(v===""?null:Number(v)):v}
function removePrepItem(i){prepItems.splice(i,1);renderPrepItems()}
function getLeaveDate(){
 const v=$("leaveTime").value;if(!v)return null;const [h,m]=v.split(":").map(Number),now=new Date(),leave=new Date();leave.setHours(h,m,0,0);if(leave<=now)leave.setDate(leave.getDate()+1);return leave;
}
function planPrep(){
 const leave=getLeaveDate();if(!leave)return toast("出発時刻を入力してください");if(!prepItems.length)return toast("準備項目を追加してください");
 if(prepItems.some(x=>!x.name.trim()))return toast("項目名を入力してください");if(prepItems.some(x=>!Number.isFinite(x.mins)||x.mins<=0))return toast("各項目の時間を入力してください");
 const available=Math.max(0,Math.floor((leave-Date.now())/60000));$("prepRemaining").textContent=available+"分";
 const items=prepItems.map(x=>({...x,include:false}));let rem=available;
 const must=items.filter(x=>x.priority==="must"),prefer=items.filter(x=>x.priority==="prefer"),optional=items.filter(x=>x.priority==="optional");
 must.forEach(x=>{x.include=true;rem-=x.mins});prefer.forEach(x=>{if(x.mins<=rem){x.include=true;rem-=x.mins}});optional.forEach(x=>{if(x.mins<=rem){x.include=true;rem-=x.mins}});
 prepPlan=items;const mustTotal=must.reduce((a,x)=>a+x.mins,0),selected=items.filter(x=>x.include);
 $("prepMessage").textContent=mustTotal>available?"必須の作業だけでも残り時間を超えています。時間は自動変更していません。":selected.length===items.length?"すべての項目を実行できそうです。設定時間をそのまま使えます。":"残り時間に合わせて優先度順に提案しました。チェックを変更して調整できます。";
 $("prepPlan").innerHTML=items.map((x,i)=>`<div class="prep-item"><label><input type="checkbox" ${x.include?"checked":""} onchange="togglePrepPlan(${i},this.checked)"><span class="grow"><strong>${esc(x.name)}</strong><div class="small">${x.mins}分 ・ ${priorityLabels[x.priority]}</div></span></label></div>`).join("");
 $("prepResult").classList.remove("hidden");updatePrepTotal();prepEnd=leave.getTime();
}
function togglePrepPlan(i,checked){if(!prepPlan[i])return;if(prepPlan[i].priority==="must"&&!checked&&!confirm("必須の項目です。本当に外しますか？")){planPrep();return}prepPlan[i].include=checked;updatePrepTotal()}
function updatePrepTotal(){
 const total=prepPlan.filter(x=>x.include).reduce((a,x)=>a+x.mins,0);$("prepTotal").textContent=total+"分";
 const leave=getLeaveDate(),available=leave?Math.max(0,Math.floor((leave-Date.now())/60000)):0;$("prepDifference").textContent=total>available?"予定時間を"+(total-available)+"分超えています。":(available-total)+"分の余裕があります。";
}
function acceptPrepPlan(){
 const selected=prepPlan.filter(x=>x.include);if(!selected.length)return toast("実行する項目を選んでください");const leave=getLeaveDate();if(!leave)return toast("出発時刻を確認してください");
 const available=Math.max(0,Math.floor((leave-Date.now())/60000)),total=selected.reduce((a,x)=>a+x.mins,0);if(total>available&&!confirm("選択した項目の合計時間が残り時間を超えています。それでも開始しますか？"))return;
 clearInterval(prepInterval);prepRun={items:selected.map(x=>({...x})),index:0,paused:false,elapsed:0,stepStarted:Date.now(),leaveAt:leave.getTime(),totalElapsed:0};
 $("prepRunnerCard").classList.remove("hidden");showPage("prep");$("prepRunnerCard").classList.remove("hidden");updatePrepRunner();startPrepInterval();$("prepRunnerCard").scrollIntoView({behavior:"smooth",block:"start"});toast("準備タイマーを開始しました");
}
function prepStepElapsed(){return prepRun?prepRun.elapsed+(prepRun.paused?0:Date.now()-prepRun.stepStarted):0}
function updatePrepRunner(){
 if(!prepRun)return;const x=prepRun.items[prepRun.index];if(!x)return;
 $("prepStepCount").textContent=(prepRun.index+1)+"/"+prepRun.items.length;$("prepCurrentStep").textContent=x.name;$("prepPlanned").textContent="設定時間 "+fmtTime(Number(x.mins)*60);$("prepPauseBtn").textContent=prepRun.paused?"再開":"一時停止";$("prepProgress").style.width=(prepRun.index/prepRun.items.length*100)+"%";updatePrepTimer();
}
function updatePrepTimer(){
 if(!prepRun)return;const x=prepRun.items[prepRun.index];if(!x)return;const elapsed=prepStepElapsed()/1000,planned=Number(x.mins)*60,remain=Math.ceil(planned-elapsed),over=remain<0;
 $("prepClock").textContent=over?"+"+fmtTime(-remain):fmtTime(remain);$("prepClock").classList.toggle("over",over);$("prepRing").classList.toggle("over",over);$("prepRing").style.setProperty("--ring-progress",(Math.max(0,Math.min(1,(planned-elapsed)/planned))*100)+"%");
 $("prepStatus").textContent=over?"予定時間を超過":"残り時間";$("prepOver").textContent=over?"予定より "+fmtTime(-remain)+" 超過":"";$("prepElapsed").textContent="実際にかかった時間 "+fmtTime(Math.floor(elapsed));
}
function startPrepInterval(){clearInterval(prepInterval);prepInterval=setInterval(()=>{if(prepRun)updatePrepTimer()},250)}
function pausePrepClock(){if(!prepRun)return;if(!prepRun.paused){prepRun.elapsed=prepStepElapsed();prepRun.paused=true}else{prepRun.paused=false;prepRun.stepStarted=Date.now()}updatePrepRunner()}
function nextPrepStep(){
 if(!prepRun)return;const current=prepRun.items[prepRun.index],elapsed=Math.floor(prepStepElapsed()/1000);prepRun.totalElapsed+=elapsed;logSeconds(elapsed,"準備",current.name);prepRun.index++;
 if(prepRun.index>=prepRun.items.length){clearInterval(prepInterval);prepInterval=null;prepRun=null;$("prepRunnerCard").classList.add("hidden");toast("準備完了！おつかれさま ♡");render();return}
 prepRun.elapsed=0;prepRun.paused=false;prepRun.stepStarted=Date.now();updatePrepRunner();startPrepInterval();
}
function stopPrepClock(){
 if(prepRun){const elapsed=Math.floor(prepStepElapsed()/1000);if(elapsed>0)logSeconds(elapsed,"準備",prepRun.items[prepRun.index].name)}
 clearInterval(prepInterval);prepInterval=null;prepRun=null;$("prepRunnerCard").classList.add("hidden");
}

/* タスクタイマー */
let activeTask=null,taskInterval=null;
function startTaskTimer(id){
 const t=db.tasks.find(x=>String(x.id)===String(id));if(!t)return;
 if(activeTask){if(!confirm("計測中のタイマーを切り替えますか？"))return;stopTaskTimer(false)}
 activeTask={id:t.id,name:t.name,cat:t.cat,started:Date.now()};$("activeTimerCard").classList.remove("hidden");$("activeTimerName").textContent=t.name;showPage("tasks");
 clearInterval(taskInterval);taskInterval=setInterval(updateTaskClock,1000);updateTaskClock();
}
function updateTaskClock(){if(activeTask)$("activeTimerClock").textContent=fmtTime(Math.floor((Date.now()-activeTask.started)/1000))}
function stopTaskTimer(shouldSave){
 clearInterval(taskInterval);taskInterval=null;if(activeTask&&shouldSave){logSeconds(Math.floor((Date.now()-activeTask.started)/1000),activeTask.cat,activeTask.name);toast("時間を記録しました")}
 activeTask=null;$("activeTimerCard").classList.add("hidden");render();
}

/* 5分集中 */
let focusInterval=null,focusEnd=0;
function startFocus(){
 stopFocus(false);focusEnd=Date.now()+5*60*1000;
 focusInterval=setInterval(()=>{const rem=Math.max(0,Math.ceil((focusEnd-Date.now())/1000));$("focusClock").textContent=fmtTime(rem);if(rem<=0){clearInterval(focusInterval);focusInterval=null;logSeconds(300,"集中","5分集中");toast("5分間おつかれさま！");render()}},250);toast("5分集中スタート！");
}
function stopFocus(reset=true){clearInterval(focusInterval);focusInterval=null;if(reset)$("focusClock").textContent="05:00"}
function logSeconds(sec,cat,name){
 if(sec<=0)return;if(!Array.isArray(db.records[dateKey()]))db.records[dateKey()]=[];
 db.records[dateKey()].push({sec:Math.max(0,Number(sec)||0),cat:cat||"その他",name:name||"",at:new Date().toISOString()});save();
}/* 勉強タイマー */
let studyTimer=null,studyStartedAt=0,studyElapsedBefore=0,studyPaused=false,studyInterval=null;
let studyMonth=new Date(new Date().getFullYear(),new Date().getMonth(),1);
let studySelectedDate=dateKey();
let scanStream=null,scanLoop=null;

function startStudyTimer(){
 if(studyTimer)return;
 studyStartedAt=Date.now();studyElapsedBefore=0;studyPaused=false;
 studyTimer={subject:$("studySubject").value,materialId:$("studyMaterial").value,goalId:$("studyGoal").value,taskId:$("studyTask").value};
 $("studySubject").disabled=true;$("studyMaterial").disabled=true;$("studyGoal").disabled=true;$("studyTask").disabled=true;
 $("studyStartBtn").disabled=true;$("studyPauseBtn").disabled=false;$("studyFinishBtn").disabled=false;
 $("studyTimerStatus").textContent="計測中";studyInterval=setInterval(updateStudyClock,250);updateStudyClock();
}
function studyElapsedMs(){return studyElapsedBefore+(studyPaused?0:Date.now()-studyStartedAt)}
function updateStudyClock(){
 if(!studyTimer)return;const sec=Math.floor(studyElapsedMs()/1000);
 $("studyClock").textContent=fmtStudyTime(sec);$("studyRing").style.setProperty("--study-progress",(sec%3600/3600*360)+"deg");$("studyClockHint").textContent="勉強中";
}
function pauseStudyTimer(){
 if(!studyTimer)return;
 if(!studyPaused){studyElapsedBefore=studyElapsedMs();studyPaused=true;$("studyPauseBtn").textContent="再開";$("studyTimerStatus").textContent="一時停止中"}
 else{studyStartedAt=Date.now();studyPaused=false;$("studyPauseBtn").textContent="一時停止";$("studyTimerStatus").textContent="計測中"}
 updateStudyClock();
}
function finishStudyTimer(){
 if(!studyTimer)return;const sec=Math.floor(studyElapsedMs()/1000);
 clearInterval(studyInterval);studyInterval=null;
 if(sec>0){
  const ended=new Date(),started=new Date(ended.getTime()-studyElapsedMs());
  db.studySessions.push({id:uid(),date:dateKey(ended),subject:studyTimer.subject,materialId:studyTimer.materialId||"",goalId:studyTimer.goalId||"",taskId:studyTimer.taskId||"",sec,startedAt:started.toISOString(),endedAt:ended.toISOString(),source:"timer"});
  logSeconds(sec,"勉強",studyTimer.subject);save();toast(minutesText(sec)+"を勉強記録に保存しました");
 }else toast("1秒未満のため記録しませんでした");
 resetStudyTimerUI();renderStudy();renderHome();renderReview();
}
function resetStudyTimerUI(){
 studyTimer=null;studyElapsedBefore=0;studyPaused=false;
 $("studySubject").disabled=false;$("studyMaterial").disabled=false;$("studyGoal").disabled=false;$("studyTask").disabled=false;
 $("studyStartBtn").disabled=false;$("studyPauseBtn").disabled=true;$("studyFinishBtn").disabled=true;
 $("studyPauseBtn").textContent="一時停止";$("studyTimerStatus").textContent="待機中";$("studyClock").textContent="00:00:00";$("studyClockHint").textContent="今日の積み重ね";$("studyRing").style.setProperty("--study-progress","0deg");
}

/* 手動で勉強記録を追加 */
function addManualStudyRecord(){
 const date=$("manualStudyDate").value;
 const subject=$("manualStudySubject").value;
 const hours=Number($("manualStudyHours").value);
 const minutes=Number($("manualStudyMinutes").value);
 const materialId=$("manualStudyMaterial").value;
 const goalId=$("manualStudyGoal").value;
 const taskId=$("manualStudyTask").value;

 if(!date)return toast("勉強した日付を選択してください");
 if(!Number.isInteger(hours)||hours<0||hours>24)return toast("時間は0〜24の整数で入力してください");
 if(!Number.isInteger(minutes)||minutes<0||minutes>59)return toast("分は0〜59の整数で入力してください");

 const sec=(hours*60+minutes)*60;
 if(sec<=0)return toast("勉強時間を入力してください");
 if(sec>24*60*60)return toast("1日24時間以内で入力してください");

 const selectedDate=new Date(date+"T00:00:00");
 if(Number.isNaN(selectedDate.getTime()))return toast("日付を確認してください");

 const session={
  id:uid(),date,subject,materialId:materialId||"",goalId:goalId||"",taskId:taskId||"",
  sec,startedAt:new Date(selectedDate.getTime()).toISOString(),
  endedAt:new Date(selectedDate.getTime()+sec*1000).toISOString(),
  source:"manual"
 };

 db.studySessions.push(session);

 // ホームの記録時間にも反映
 if(!Array.isArray(db.records[date]))db.records[date]=[];
 db.records[date].push({sec,cat:"勉強",name:subject,at:new Date().toISOString(),source:"manual-study",studySessionId:session.id});

 save();

 // 入力欄を初期化
 $("manualStudyHours").value="0";
 $("manualStudyMinutes").value="30";
 $("manualStudyDate").value=dateKey();

 // 追加した日付のカレンダーを表示
 studyMonth=new Date(selectedDate.getFullYear(),selectedDate.getMonth(),1);
 studySelectedDate=date;
 renderStudy();renderHome();renderReview();

 toast(date+"の勉強記録を追加しました ♡");
}

function sessionsForMonth(y,m){
 return db.studySessions.filter(s=>{const d=new Date(s.date+"T00:00:00");return d.getFullYear()===y&&d.getMonth()===m});
}
function totalStudySeconds(sessions){return sessions.reduce((a,s)=>a+Math.max(0,Number(s.sec)||0),0)}
function renderStudy(){
 const goals=$("studyGoal"),tasks=$("studyTask"),materials=$("studyMaterial");
 if(!goals||!tasks||!materials)return;
 const oldGoal=goals.value,oldTask=tasks.value,oldMaterial=materials.value;
 goals.innerHTML='<option value="">選択なし</option>'+db.goals.map(g=>`<option value="${esc(g.id)}">${esc(g.name)}</option>`).join("");
 tasks.innerHTML='<option value="">選択なし</option>'+db.tasks.map(t=>`<option value="${esc(t.id)}">${esc(t.name)}</option>`).join("");
 materials.innerHTML='<option value="">教材を選択（任意）</option>'+db.materials.map(m=>`<option value="${esc(m.id)}">${esc(m.title)}</option>`).join("");
 if(db.goals.some(g=>g.id===oldGoal))goals.value=oldGoal;
 if(db.tasks.some(t=>t.id===oldTask))tasks.value=oldTask;
 if(db.materials.some(m=>m.id===oldMaterial))materials.value=oldMaterial;

 // 手動入力フォームの選択肢
 const manualMaterial=$("manualStudyMaterial"),manualGoal=$("manualStudyGoal"),manualTask=$("manualStudyTask");
 const oldMM=manualMaterial.value,oldMG=manualGoal.value,oldMT=manualTask.value;
 manualMaterial.innerHTML='<option value="">選択なし</option>'+db.materials.map(m=>`<option value="${esc(m.id)}">${esc(m.title)}</option>`).join("");
 manualGoal.innerHTML='<option value="">選択なし</option>'+db.goals.map(g=>`<option value="${esc(g.id)}">${esc(g.name)}</option>`).join("");
 manualTask.innerHTML='<option value="">選択なし</option>'+db.tasks.map(t=>`<option value="${esc(t.id)}">${esc(t.name)}</option>`).join("");
 if(db.materials.some(m=>m.id===oldMM))manualMaterial.value=oldMM;
 if(db.goals.some(g=>g.id===oldMG))manualGoal.value=oldMG;
 if(db.tasks.some(t=>t.id===oldMT))manualTask.value=oldMT;

 if(!$("manualStudyDate").value)$("manualStudyDate").value=dateKey();

 const now=new Date(),weekStart=new Date(now);
 weekStart.setDate(now.getDate()-((now.getDay()+6)%7));weekStart.setHours(0,0,0,0);
 const week=db.studySessions.filter(s=>new Date(s.date+"T00:00:00")>=weekStart&&new Date(s.date+"T00:00:00")<=now);
 const month=sessionsForMonth(now.getFullYear(),now.getMonth());
 $("studyWeekTotal").textContent=minutesText(totalStudySeconds(week));
 $("studyMonthTotal").textContent=minutesText(totalStudySeconds(month));
 renderStudySubjects(month);renderStudyCalendar();renderMaterials();renderShareCard();
}
function renderStudySubjects(sessions){
 const totals={};sessions.forEach(s=>totals[s.subject]=(totals[s.subject]||0)+Number(s.sec||0));
 const list=Object.entries(totals).sort((a,b)=>b[1]-a[1]);
 if(!list.length){$("studySubjectStats").innerHTML='<div class="empty">まだ今月の勉強記録がありません。</div>';return}
 const max=Math.max(...list.map(x=>x[1]),1);
 $("studySubjectStats").innerHTML=list.map(([name,sec])=>`<div class="study-bar-row"><span>${esc(name)}</span><div class="study-bar"><span style="width:${sec/max*100}%"></span></div><strong>${minutesText(sec)}</strong></div>`).join("");
}
function changeStudyMonth(delta){studyMonth=new Date(studyMonth.getFullYear(),studyMonth.getMonth()+delta,1);renderStudyCalendar()}
function renderStudyCalendar(){
 const y=studyMonth.getFullYear(),m=studyMonth.getMonth(),first=new Date(y,m,1),last=new Date(y,m+1,0);
 $("studyMonthLabel").textContent=y+"年"+(m+1)+"月";
 const dayNames=["月","火","水","木","金","土","日"];let html=dayNames.map(d=>`<div class="calendar-head">${d}</div>`).join("");
 const offset=(first.getDay()+6)%7;for(let i=0;i<offset;i++)html+="<div></div>";
 for(let day=1;day<=last.getDate();day++){
  const d=new Date(y,m,day),key=dateKey(d),sessions=db.studySessions.filter(s=>s.date===key),sec=totalStudySeconds(sessions);
  const cls=["calendar-day",key===dateKey()?"today":"",key===studySelectedDate?"selected":""].filter(Boolean).join(" ");
  html+=`<button class="${cls}" onclick="selectStudyDate('${key}')"><strong>${day}</strong><span>${sec?minutesText(sec):""}</span>${sec?'<i class="dot"></i>':""}</button>`;
 }
 $("studyCalendar").innerHTML=html;renderStudyDay();
}
function selectStudyDate(key){studySelectedDate=key;renderStudyCalendar()}
function renderStudyDay(){
 $("studySelectedDay").textContent=studySelectedDate+" の記録";
 const list=db.studySessions.filter(s=>s.date===studySelectedDate);
 if(!list.length){$("studyDaySessions").innerHTML='<div class="empty">この日の勉強記録はありません。</div>';return}
 $("studyDaySessions").innerHTML=list.map(s=>{
  const material=db.materials.find(m=>m.id===s.materialId);
  const source=s.source==="manual"?"手動入力":"タイマー";
  return `<div class="history-entry"><div class="between"><strong>${esc(s.subject)}</strong><strong>${minutesText(s.sec)}</strong></div><div class="small">${source}</div>${material?`<div class="small">${esc(material.title)}</div>`:""}<button class="btn small danger" onclick="deleteStudySession('${esc(s.id)}')">記録を削除</button></div>`;
 }).join("");
}
function deleteStudySession(id){
 if(!confirm("この勉強記録を削除しますか？"))return;
 const target=db.studySessions.find(s=>s.id===id);
 db.studySessions=db.studySessions.filter(s=>s.id!==id);
 // ホームの記録時間からも該当する手動記録を削除
 if(target&&target.source==="manual"){
  const records=db.records[target.date]||[];
  db.records[target.date]=records.filter(r=>r.studySessionId!==id);
 }
 save();renderStudy();renderHome();
}
function toggleMaterialForm(){$("materialForm").classList.toggle("hidden")}
function validISBN(v){
 const s=String(v||"").replace(/[-\s]/g,"");
 if(/^\d{13}$/.test(s)){let sum=0;for(let i=0;i<12;i++)sum+=Number(s[i])*(i%2?3:1);return (10-sum%10)%10===Number(s[12])}
 if(/^\d{9}[\dX]$/.test(s)){let sum=0;for(let i=0;i<10;i++)sum+=(s[i]==="X"?10:Number(s[i]))*(10-i);return sum%11===0}
 return false;
}
function addStudyMaterial(){
 const title=$("materialTitle").value.trim(),isbn=$("materialISBN").value.trim().replace(/[-\s]/g,"");
 if(!title)return toast("教材名を入力してください");if(isbn&&!validISBN(isbn))return toast("ISBNの形式を確認してください");
 db.materials.push({id:uid(),title,isbn,subject:$("materialSubject").value,createdAt:new Date().toISOString()});
 $("materialTitle").value="";$("materialISBN").value="";$("materialForm").classList.add("hidden");stopISBNScan();save();renderStudy();toast("教材を登録しました");
}
function renderMaterials(){
 const el=$("materialList");if(!db.materials.length){el.innerHTML='<div class="empty">教材はまだ登録されていません。</div>';return}
 el.innerHTML=db.materials.map(m=>`<div class="material-item"><div class="between"><strong>${esc(m.title)}</strong><button class="btn small danger" onclick="deleteMaterial('${esc(m.id)}')">削除</button></div><div class="small">${esc(m.subject)}${m.isbn?" ・ ISBN "+esc(m.isbn):""}</div></div>`).join("");
}
function deleteMaterial(id){
 if(!confirm("この教材を削除しますか？勉強記録自体は残ります。"))return;
 db.materials=db.materials.filter(m=>m.id!==id);save();renderStudy();
}
async function startISBNScan(){
 const video=$("scanVideo"),area=$("scanArea"),message=$("scanMessage");area.classList.remove("hidden");
 if(!("BarcodeDetector" in window)){message.textContent="このブラウザではバーコード読み取りに対応していません。ISBNを手入力してください。";return}
 try{
  const detector=new BarcodeDetector({formats:["ean_13"]});scanStream=await navigator.mediaDevices.getUserMedia({video:{facingMode:"environment"}});
  video.srcObject=scanStream;message.textContent="本のバーコードをカメラに映してください。";
  const scan=async()=>{
   if(!scanStream)return;
   try{const codes=await detector.detect(video);const code=codes.find(c=>String(c.rawValue).startsWith("978")||String(c.rawValue).startsWith("979"));
    if(code){$("materialISBN").value=code.rawValue;message.textContent="読み取りました。教材名と科目を入力して保存してください。";stopISBNScan();return}
   }catch(e){}
   scanLoop=requestAnimationFrame(scan);
  };
  scanLoop=requestAnimationFrame(scan);
 }catch(e){message.textContent="カメラを起動できませんでした。カメラの許可を確認するか、ISBNを手入力してください。"}
}
function stopISBNScan(){
 if(scanLoop)cancelAnimationFrame(scanLoop);scanLoop=null;
 if(scanStream){scanStream.getTracks().forEach(t=>t.stop());scanStream=null}
 const v=$("scanVideo");if(v)v.srcObject=null;
}
function renderShareCard(){
 const theme=$("shareTheme").value;
 const colors={beige:{bg:"#f1e9df",ink:"#51463f"},lavender:{bg:"#eee5f8",ink:"#453c50"},mono:{bg:"#eeeeee",ink:"#333333"}};
 const c=colors[theme]||colors.beige,card=$("studyShareCard");card.style.background=c.bg;card.style.color=c.ink;
 $("shareDate").textContent=new Date().toLocaleDateString("ja-JP",{year:"numeric",month:"long",day:"numeric"});
 const sec=totalStudySeconds(db.studySessions.filter(s=>s.date===dateKey()));$("shareTime").textContent=minutesText(sec);$("shareCommentPreview").textContent=$("shareComment").value.trim();
}
async function saveStudyShareCard(){
 renderShareCard();const card=$("studyShareCard"),rect=card.getBoundingClientRect(),scale=3;
 const canvas=document.createElement("canvas");canvas.width=rect.width*scale;canvas.height=rect.height*scale;
 const ctx=canvas.getContext("2d");ctx.scale(scale,scale);
 const style=getComputedStyle(card),cx=rect.width/2,cy=rect.height/2,r=Math.min(rect.width,rect.height)/2-4;
 ctx.fillStyle=style.backgroundColor;ctx.beginPath();ctx.arc(cx,cy,r,0,Math.PI*2);ctx.fill();
 ctx.strokeStyle=getComputedStyle(document.documentElement).getPropertyValue("--paper");ctx.lineWidth=8;ctx.stroke();
 ctx.fillStyle=style.color;ctx.textAlign="center";ctx.textBaseline="middle";
 ctx.font="11px sans-serif";ctx.fillText("MY STUDY LOG",cx,cy-65);
 ctx.font="13px sans-serif";ctx.fillText($("shareDate").textContent,cx,cy-35);
 ctx.font="bold 42px sans-serif";ctx.fillText($("shareTime").textContent,cx,cy+5);
 ctx.font="11px sans-serif";ctx.fillText("A LITTLE PROGRESS EVERY DAY",cx,cy+43);
 const comment=$("shareComment").value.trim();if(comment){ctx.font="13px sans-serif";ctx.fillText(comment.slice(0,40),cx,cy+72)}
 canvas.toBlob(blob=>{
  if(!blob)return toast("画像を作成できませんでした");
  const url=URL.createObjectURL(blob),a=document.createElement("a");a.href=url;a.download="FLOW-study-"+dateKey()+".png";a.click();setTimeout(()=>URL.revokeObjectURL(url),1500);toast("共有カードを保存しました");
 },"image/png");
}
$("shareComment")?.addEventListener("input",()=>{if($("page-study").classList.contains("active"))renderShareCard()});

/* 振り返り */
function loadTodayReflection(){
 const r=db.reflection[dateKey()]||{};$("reflectionWin").value=r.win||"";$("reflectionBlock").value=r.block||"";$("reflectionNext").value=r.next||"";$("reflectionSaved").textContent=r.saved?"今日の振り返りは保存済み ♡":"";
}
function saveReflection(){
 db.reflection[dateKey()]={win:$("reflectionWin").value,block:$("reflectionBlock").value,next:$("reflectionNext").value,saved:true,updatedAt:new Date().toISOString()};
 save();$("reflectionSaved").textContent="保存しました ♡";renderReview();toast("振り返りを保存しました");
}
let historyOpen=false;
function toggleReflectionHistory(){
 historyOpen=!historyOpen;$("reflectionHistory").classList.toggle("hidden",!historyOpen);$("historyToggle").textContent=historyOpen?"履歴を閉じる":"履歴を見る";if(historyOpen)renderReflectionHistory();
}
function renderReflectionHistory(){
 const el=$("reflectionHistory"),entries=Object.entries(db.reflection||{}).filter(([k,r])=>k!==dateKey()&&r&&r.saved).sort((a,b)=>b[0].localeCompare(a[0]));
 if(!entries.length){el.innerHTML='<div class="empty">まだ過去の振り返りはありません。</div>';return}
 el.innerHTML=entries.map(([k,r])=>`<details class="history-entry"><summary>${esc(k)}</summary><label>できたこと</label><textarea id="hist-win-${esc(k)}">${esc(r.win||"")}</textarea><label>困ったこと</label><textarea id="hist-block-${esc(k)}">${esc(r.block||"")}</textarea><label>明日やりたいこと</label><textarea id="hist-next-${esc(k)}">${esc(r.next||"")}</textarea><button class="btn primary small" onclick="updateOldReflection('${esc(k)}')">この記録を更新</button></details>`).join("");
}
function updateOldReflection(k){
 const r=db.reflection[k];if(!r)return;const a=$("hist-win-"+k),b=$("hist-block-"+k),c=$("hist-next-"+k);if(!a||!b||!c)return;
 db.reflection[k]={...r,win:a.value,block:b.value,next:c.value,updatedAt:new Date().toISOString()};save();toast("過去の記録を更新しました");
}
function renderReview(){
 $("reviewDone").textContent=todayTasks().filter(t=>t.done).length;$("reviewTime").textContent=minutesText(todaySeconds());if(historyOpen)renderReflectionHistory();
}

/* 設定・バックアップ */
function changeTheme(theme){db.theme=theme;save();applyTheme();toast("テーマを変更しました")}
function exportData(){
 save();const blob=new Blob([JSON.stringify(db,null,2)],{type:"application/json"}),url=URL.createObjectURL(blob),a=document.createElement("a");
 a.href=url;a.download="FLOW-backup-"+dateKey()+".json";document.body.appendChild(a);a.click();a.remove();setTimeout(()=>URL.revokeObjectURL(url),1000);toast("バックアップを作成しました");
}
function importData(){
 const file=$("importFile").files[0];if(!file)return toast("バックアップファイルを選んでください");
 if(!confirm("現在のデータを、選択したバックアップの内容に置き換えますか？"))return;
 const reader=new FileReader();
 reader.onload=()=>{
  try{
   const parsed=JSON.parse(reader.result);if(!parsed||typeof parsed!=="object"||Array.isArray(parsed))throw Error("invalid");
   db=normalize(parsed);save();historyOpen=false;$("reflectionHistory").classList.add("hidden");cancelRoutineEdit();render();loadTodayReflection();toast("バックアップを復元しました");
  }catch(e){toast("ファイルを読み込めませんでした。FLOWのバックアップか確認してください")}
 };
 reader.onerror=()=>toast("ファイルを読み込めませんでした");reader.readAsText(file);
}
function resetApp(){
 if(!confirm("本当に初期化しますか？先にバックアップを取ってください。"))return;
 if(!confirm("タスク・目標・記録・振り返りを含めて初期化します。続けますか？"))return;
 stopTaskTimer(false);stopRoutine();stopFocus(false);stopPrepClock();stopISBNScan();
 if(studyTimer){clearInterval(studyInterval);studyTimer=null}
 db=fresh();save();historyOpen=false;$("reflectionHistory").classList.add("hidden");prepItems=[];renderPrepItems();cancelRoutineEdit();render();loadTodayReflection();showPage("home");toast("初期化しました");
}

/* 起動 */
function dailyMaintenance(){
 if(!db.dailyTasks)db.dailyTasks={};
 if(!db.dailyTasks[dateKey()])db.dailyTasks[dateKey()]={};
}
dailyMaintenance();save();render();loadTodayReflection();renderPrepItems();
</script>
</body>
</html>