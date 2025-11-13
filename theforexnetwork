<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>The Forex Network / Fix-LP</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
<style>
  /* --- আগের ডিজাইন স্টাইলস (রং/বাটন/ফ্লোটিং লোগো) --- */
  body { margin:0; padding:0; font-family:'Poppins',sans-serif; background: linear-gradient(200deg, red, white, red, white); color:#333; display:flex; justify-content:center; align-items:flex-start; min-height:100vh; overflow-y:auto; scroll-behavior:smooth;}
  .container { width:100%; max-width:500px; background:rgba(255,255,255,0.95); border-radius:20px; box-shadow:0 8px 50px rgba(0,0,0,0.2); padding:25px 20px 50px 20px; backdrop-filter:blur(10px); margin:60px auto 80px auto;}
  .floating-logo { position:fixed; top:5px; left:50%; transform:translateX(-50%); background:white; border-radius:50%; box-shadow:0 4px 15px rgba(0,0,0,0.2); padding:8px; z-index:1000;}
  .floating-logo img { width:70px; height:70px; border-radius:50%; object-fit:cover; }
  h1 { font-size:24px; background: linear-gradient(90deg, #1e3c72, #2a5298); -webkit-background-clip:text; color:transparent; margin-bottom:20px; text-align:center; }
  .menu { display:flex; flex-wrap:wrap; justify-content:space-around; margin:10px 0; }
  .menu button { flex:1 1 30%; margin:5px; padding:10px; border-radius:12px; border:none; background: linear-gradient(90deg,#1e3c72,#2a5298); color:#fff; font-weight:600; cursor:pointer; transition:0.3s; }
  .menu button:hover { opacity:0.9; }
  .hidden { display:none; }
  input,select,button,textarea { width:100%; padding:10px; margin:8px 0; border-radius:12px; border:1px solid #ccc; box-sizing:border-box; }
  input:focus, select:focus, textarea:focus { border-color:#2a5298; box-shadow:0 0 6px rgba(42,82,152,0.4); outline:none; }
  .balance-card { background: linear-gradient(135deg,#e0f7fa,#b2ebf2); padding:15px; border-radius:15px; text-align:center; font-size:18px; font-weight:600; color:#006064; margin:10px 0 10px; }
  .notice-card { background:#fff3e0; padding:12px; border-radius:12px; margin-bottom:15px; color:#e65100; font-weight:500; }
  .task, .trans { border:1px solid #ddd; padding:12px; border-radius:12px; background:#fff; margin:10px 0; }
  .task:hover, .trans:hover { background:#f3f0ff; }
  table { width:100%; border-collapse:collapse; font-size:14px; background:#fff; border-radius:10px; overflow:hidden; margin:10px 0; }
  th, td { padding:8px; text-align:left; border-bottom:1px solid #eee; }
  th { background:#2a5298; color:#fff; font-weight:600; }
  tr:nth-child(even){ background:#fafafa; }
  .action-btn { display:inline-block; margin:2px; padding:6px 10px; border:none; border-radius:8px; color:#fff; font-size:13px; font-weight:500; cursor:pointer; }
  .approve { background:#4caf50; }
  .reject { background:#e53935; }
  .block, .unblock { background:#4caf50; }
  .delete { background:#ff5252; }
  .card { background:rgba(255,255,255,0.95); padding:15px; border-radius:15px; box-shadow:0 3px 10px rgba(0,0,0,0.08); margin-bottom:15px; }
  #helpList, #adminHelpList { max-height:250px; overflow-y:auto; }
  #signupDiv button{ background: linear-gradient(90deg,#ff416c,#ff4b2b); color:#fff; font-weight:600; }
  #loginDiv button{ background: linear-gradient(90deg,#36d1dc,#5b86e5); color:#fff; font-weight:600; }
  @media(max-width:760px){ .menu button{ flex:1 1 45%; } .container{ padding:20px; } }
  .small { font-size:13px; color:#555; }
  .status-pill { display:inline-block; padding:6px 8px; border-radius:999px; font-weight:600; font-size:12px; color:#fff; }
  .status-pending { background:#ffb74d; }
  .status-approved { background:#4caf50; }
  .status-rejected { background:#e53935; }
</style>
</head>
<body>
  <div class="floating-logo"><img src="logo.png" id="platformLogo" alt="Logo"></div>

  <div class="container" id="auth-section">
    <h1>The Forex Network</h1>

    <!-- AUTH -->
    <div id="authDiv">
      <div id="signupDiv">
        <h2>Sign Up</h2>
        <input type="text" id="signupName" placeholder="Full Name">
        <input type="text" id="signupPhone" placeholder="Phone Number">
        <input type="password" id="signupPass" placeholder="Password">
        <input type="text" id="signupRefCode" placeholder="Referral Code (1234)">
        <button onclick="signup()">Sign Up</button>
        <p>Already have an account? <a href="#" onclick="showLogin()">Login</a></p>
      </div>

      <div id="loginDiv" class="hidden">
        <h3>Login</h3>
        <input type="text" id="loginPhone" placeholder="Phone Number">
        <input type="password" id="loginPass" placeholder="Password">
        <button onclick="login()">Login</button>
        <p>Don't have an account? <a href="#" onclick="showSignup()">Sign Up</a></p>
      </div>
    </div>

    <!-- USER DASHBOARD -->
    <div id="userDashboard" class="hidden">
      <div style="text-align:right;"><button style="background:#e53935;color:#fff;padding:8px;border-radius:8px;border:none;" onclick="logout()">Logout</button></div>
      <h3>Welcome, <span id="userName"></span></h3>
      <div class="balance-card">Balance: ৳ <span id="userBalance">0</span></div>
      <div id="userNotice" class="notice-card hidden"></div>

      <div class="menu">
        <button onclick="goHome()">Home</button>
        <button onclick="showSection('plans')">My Plan</button>
        <button onclick="showSection('deposit')">Deposit</button>
        <button onclick="showSection('withdraw')">Withdraw</button>
        <button onclick="showSection('transactions')">Transactions</button>
         <button onclick="showSection('refer')">My Team</button>
        <button onclick="showSection('tasks')">My Work</button>
        <button onclick="showSection('account')">Settings</button>
        <button onclick="showSection('support')">Support</button>
      
      </div>

      <div id="home"><h2>Welcome to, The Forex Network</h2><p class="small">Complete Work, earn money, and grow your business efficiently.</p></div>

      <div id="plans" class="hidden">
        <h2>Buy a Plan</h2>
        <div id="currentPlanInfo" class="card"></div>
        <div class="card"><h4>৳300 Plan</h4><p class="small">3 Tasks/day • ৳ per task: determined by admin</p><button onclick="buyPlan(300)">Buy Now (৳300)</button></div>
        <div class="card"><h4>৳1000 Plan</h4><p class="small">10 Tasks/day • ৳ per task: determined by admin</p><button onclick="buyPlan(1000)">Buy Now (৳1000)</button></div>
      </div>

      <div id="tasks" class="hidden"><h2>My Work</h2><div id="taskList"></div></div>

      <div id="deposit" class="hidden">
        <h2>Deposit</h2>
        <h4 class="small">Bkash/Nagad No: <b>01734625071</b></h4>
        <select id="depositMethod"><option>Bkash</option><option>Nagad</option></select>
        <input type="number" id="depositAmount" placeholder="Amount">
        <input type="text" id="depositCode" placeholder="Transaction Code">
        <button onclick="deposit()">Deposit</button>
      </div>

      <div id="withdraw" class="hidden">
        <h2>Withdraw</h2>
        <p class="small">নোট: প্রথমবার উইথড্র করার জন্য আপনার রেফার করা কমপক্ষে ৫ জনকে আপনার রেফার কোড ব্যবহার করে সাইনআপ করে এবং প্ল্যান ক্রয় করতে হবে।</p>
        <select id="withdrawMethod"><option>Bkash</option><option>Nagad</option></select>
        <input type="text" id="withdrawNumber" placeholder="Your Number">
        <input type="number" id="withdrawAmount" placeholder="Amount (minimum ৳1000)">
        <button onclick="withdraw()">Withdraw</button>
      </div>

      <div id="transactions" class="hidden"><h2>Transaction History</h2>
        <div class="card">
          <h4>Deposit History</h4>
          <div id="depositHistory"></div>
        </div>
        <div class="card">
          <h4>Withdraw History</h4>
          <div id="withdrawHistory"></div>
        </div>
        <div class="card">
          <h4>Plan Purchase History</h4>
          <div id="planHistory"></div>
        </div>
        <div class="card">
          <h4>Other Transactions</h4>
          <div id="otherHistory"></div>
        </div>
      </div>

      <div id="support" class="hidden">
        <h2>Support Center</h2>
        <p class="small">আপনার যেকোন সমস্যা বা প্রশ্নের জন্য মেসেজ দিন। Admin ২৪ ঘন্টার মধ্যে রিপ্লাই দিবেন।  এবং নিচে আমাদের ইনকাম রিভিউ গ্রুপ আছে দেখে আসুন,,এবং ইউটিউব ভিডিও দেখুন, এবং প্রয়োজনে টেলিগ্রাম আইডিতে এডমিনকে মেসেজ করুন ধন্যবাদ ✅</p>
        <input type="text" id="helpMessage" placeholder="Type your message">
        <button onclick="sendHelp()">Send</button>
        <div id="helpList"></div>

        <div class="card">
          <h4>Helpline/h4>
          <p>Income Review Group: <a href="#" id="reviewGroupLink" target="_blank">Visit Group</a></p>
          <p>YouTube Channel: <a href="#" id="youtubeLink" target="_blank">Visit Channel</a></p>
          <p>Admin Telegram: <a href="#" id="telegramLink" target="_blank">Message Admin</a></p>
        </div>
      </div>

      <div id="account" class="hidden">
        <h2>Account Settings</h2>
        <!-- change phone removed as requested -->
        <p class="small">Change password:</p>
        <input type="password" id="oldPass" placeholder="Current Password">
        <input type="password" id="newPass" placeholder="New Password">
        <button onclick="changePassword()">Change Password</button>
      </div>

      <div id="refer" class="hidden">
        <h2>My Refer</h2>
        <div id="myReferLink" class="card"></div>
        <div id="referHistory" class="card"></div>
      </div>

    </div>

    <!-- ADMIN PANEL -->
    <div id="adminPanel" class="hidden">
      <h2>Admin Panel</h2>
      <div style="text-align:right;margin-bottom:10px;"><button style="background:#e53935;color:#fff;padding:8px;border-radius:8px;border:none;" onclick="logout()">Logout</button></div>
      <div class="menu">
        <button onclick="showAdminSection('adminTasks')">Tasks</button>
        <button onclick="showAdminSection('adminUsers')">Users</button>
        <button onclick="showAdminSection('adminDeposits')">Deposit Requests</button>
        <button onclick="showAdminSection('adminWithdraws')">Withdraw Requests</button>
        <button onclick="showAdminSection('adminHelp')">Support Desk</button>
        <button onclick="showAdminSection('adminNotice')">Send Notice</button>
        <button onclick="showAdminSection('adminLogo')">Change Logo</button>
      </div>

      <div id="adminNotice" class="hidden card">
        <h3>Send Notice to All Users</h3>
        <input type="text" id="noticeMessage" placeholder="Type your notice here">
        <button onclick="sendNotice()">Send Notice</button>
      </div>

      <div id="adminLogo" class="hidden card">
        <h3>Change Logo</h3>
        <input type="file" id="logoInput" accept="image/*"><button onclick="changeLogo()">Upload Logo</button>
      </div>

      <div id="adminTasks" class="hidden card">
        <h3>Manage Tasks (Daily Add/Delete) + Set Reward</h3>
        <input type="text" id="taskTitle" placeholder="Task Title">
        <input type="text" id="taskLink" placeholder="Task Link (https://...)">
        <input type="number" id="taskReward" placeholder="Reward per task (৳) — e.g. 10">
        <button onclick="addTask()">Add Task</button>
        <div id="adminTaskList"></div>
      </div>

      <div id="adminUsers" class="hidden card">
        <h3>Users List</h3>
        <table id="usersTable"><thead><tr><th>Name</th><th>Phone</th><th>Balance</th><th>Password</th><th>Status</th><th>Actions</th></tr></thead><tbody></tbody></table>
      </div>

      <div id="adminDeposits" class="hidden card">
        <h3>Deposit Requests</h3>
        <table id="depositTable"><thead><tr><th>User</th><th>Amount</th><th>Method</th><th>Code</th><th>Status</th><th>Action</th></tr></thead><tbody></tbody></table>
      </div>

      <div id="adminWithdraws" class="hidden card">
        <h3>Withdraw Requests</h3>
        <table id="withdrawTable"><thead><tr><th>User</th><th>Amount</th><th>Method</th><th>Number</th><th>Status</th><th>Action</th></tr></thead><tbody></tbody></table>
      </div>

      <div id="adminHelp" class="hidden card">
        <h3>Support Desk</h3>
        <div id="adminHelpList"></div>
      </div>
    </div>

  </div>

<script>
/* =================== Data & Constants =================== */
let users = JSON.parse(localStorage.getItem('users')) || [];
let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
let deposits = JSON.parse(localStorage.getItem('deposits')) || [];
let withdraws = JSON.parse(localStorage.getItem('withdraws')) || [];
let helps = JSON.parse(localStorage.getItem('helps')) || [];
let currentUser = null;
const adminPhone = "01700000000", adminPass = "admin123";
const ONE_DAY_MS = 24 * 60 * 60 * 1000;
const FIRST_WITHDRAW_REF_REQUIRED = 5;
const MIN_WITHDRAW_AMOUNT = 1000;

/* =================== Helpers =================== */
function saveAll(){
  localStorage.setItem('users', JSON.stringify(users));
  localStorage.setItem('tasks', JSON.stringify(tasks));
  localStorage.setItem('deposits', JSON.stringify(deposits));
  localStorage.setItem('withdraws', JSON.stringify(withdraws));
  localStorage.setItem('helps', JSON.stringify(helps));
}
function findUserIndexByPhone(phone){ return users.findIndex(u=>u.phone===phone); }
function findUserByPhone(phone){ return users.find(u=>u.phone===phone); }
function todayISO(){ let d=new Date(); return d.toISOString().split('T')[0]; }
function now(){ return Date.now(); }
function generateId(prefix='id'){ return prefix + '_' + Date.now() + '_' + Math.floor(Math.random()*10000); }
function capitalize(s){ if(!s) return ''; return s.charAt(0).toUpperCase()+s.slice(1); }
function escapeHtml(unsafe) {
  if(unsafe === null || unsafe === undefined) return '';
  return unsafe.toString().replace(/[&<>"'`=\/]/g, function (s) {
    return ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;','/':'&#x2F;','`':'&#x60;','=':'&#x3D;'})[s];
  });
}
function statusPill(status){
  status = (status||'').toString().toLowerCase();
  if(status==='approved') return '<span class="status-pill status-approved">Approved</span>';
  if(status==='rejected') return '<span class="status-pill status-rejected">Rejected</span>';
  return '<span class="status-pill status-pending">Pending</span>';
}

/* =================== Load/Change Logo =================== */
function loadLogo(){ let logo = localStorage.getItem('platformLogo'); if(logo) document.getElementById('platformLogo').src = logo; }
function changeLogo(){
  let file = document.getElementById('logoInput').files[0];
  if(!file) return alert('Select image');
  let reader = new FileReader();
  reader.onload = function(e){
    localStorage.setItem('platformLogo', e.target.result);
    document.getElementById('platformLogo').src = e.target.result;
    alert('Logo changed successfully!');
  };
  reader.readAsDataURL(file);
}
loadLogo();

/* =================== Auth =================== */
function showSignup(){ document.getElementById('signupDiv').classList.remove('hidden'); document.getElementById('loginDiv').classList.add('hidden'); }
function showLogin(){ document.getElementById('signupDiv').classList.add('hidden'); document.getElementById('loginDiv').classList.remove('hidden'); }
function logout(){
  currentUser = null;
  document.getElementById('userDashboard').classList.add('hidden');
  document.getElementById('adminPanel').classList.add('hidden');
  document.getElementById('authDiv').classList.remove('hidden');
  saveAll();
}

/* Signup */
function signup(){
  let n = document.getElementById('signupName').value.trim();
  let p = document.getElementById('signupPhone').value.trim();
  let pass = document.getElementById('signupPass').value;
  let ref = document.getElementById('signupRefCode').value.trim();
  if(!n || !p || !pass) return alert('Fill all required fields');
  if(users.find(u => u.phone === p)) return alert('Phone already registered');
  users.push({
    name: n,
    phone: p,
    pass: pass,
    balance: 0,
    plan: null,
    status: 'active',
    ref: ref || '',
    transactions: [],
    tasksDone: 0,
    completedTasks: [],
    firstWithdrawDone: false
  });
  saveAll();
  alert('Sign up success! Please login.');
  showLogin();
}

/* Login */
function login(){
  let p = document.getElementById('loginPhone').value.trim();
  let pass = document.getElementById('loginPass').value;
  if(p === adminPhone && pass === adminPass){
    document.getElementById('authDiv').classList.add('hidden');
    document.getElementById('adminPanel').classList.remove('hidden');
    loadAdminTasks(); loadAdminUsers(); loadAdminDeposits(); loadAdminWithdraws(); loadAdminHelp();
    return;
  }
  let u = users.find(usr => usr.phone === p && usr.pass === pass);
  if(!u) return alert('Invalid credentials');
  if(u.status !== 'active') return alert('Your account is blocked');
  currentUser = u;
  document.getElementById('userDashboard').classList.remove('hidden');
  document.getElementById('authDiv').classList.add('hidden');
  updateDashboard();
}

/* =================== Dashboard UI =================== */
function updateDashboard(){
  document.getElementById('userName').innerText = currentUser.name;
  document.getElementById('userBalance').innerText = Number(currentUser.balance || 0).toFixed(2);
  document.getElementById('myReferLink').innerText = 'Your referral code: ' + currentUser.phone;
  document.getElementById('userNotice').classList.add('hidden');
  if(localStorage.getItem('notice')){
    document.getElementById('userNotice').classList.remove('hidden');
    document.getElementById('userNotice').innerText = localStorage.getItem('notice');
  }
  showSection('home');
  loadTasks();
  loadTransactions();
  loadCurrentPlan();
  loadReferHistory();
}
function goHome(){ showSection('home'); }
function showSection(sec){
  let sections = ['home','tasks','deposit','withdraw','transactions','plans','support','account','refer'];
  sections.forEach(s => document.getElementById(s).classList.add('hidden'));
  document.getElementById(sec).classList.remove('hidden');
  if(sec === 'transactions') loadTransactions();
  if(sec === 'refer') loadReferHistory();
}
function showAdminSection(sec){
  let sections = ['adminTasks','adminUsers','adminDeposits','adminWithdraws','adminHelp','adminNotice','adminLogo'];
  sections.forEach(s => document.getElementById(s).classList.add('hidden'));
  document.getElementById(sec).classList.remove('hidden');
}

/* =================== Plans =================== */
function buyPlan(amount){
  if(!currentUser) return alert('Login first');
  if(currentUser.plan && currentUser.plan.dateMs){
    let days = Math.floor((now() - currentUser.plan.dateMs) / ONE_DAY_MS);
    if(days < 30) return alert('You already have a plan. আপনি ৩০ দিনের মধ্যে আরেকটি প্ল্যান নিতে পারবেন না।');
  }
  if(currentUser.balance < amount) return alert('Insufficient balance to buy this plan.');
  currentUser.balance = Number((currentUser.balance - amount).toFixed(2));
  currentUser.plan = { amount: amount, dateMs: now(), tasksAllowed: Math.floor(amount / 100), lastResetISO: todayISO() };
  currentUser.tasksDone = 0;
  if(!currentUser.transactions) currentUser.transactions = [];
  currentUser.transactions.push({ type: 'Plan Purchase', amount: -amount, date: new Date().toLocaleString(), note: amount + ' ৳ plan' });
  // referral commission
  if(currentUser.ref){
    let refUser = findUserByPhone(currentUser.ref);
    if(refUser){
      let commission = Number((amount * 0.20).toFixed(2));
      refUser.balance = Number((refUser.balance + commission).toFixed(2));
      if(!refUser.transactions) refUser.transactions = [];
      refUser.transactions.push({ type: 'Referral Commission', amount: commission, date: new Date().toLocaleString(), note: '20% from ' + currentUser.phone + ' plan' });
      let idx = findUserIndexByPhone(refUser.phone);
      if(idx !== -1) users[idx] = refUser;
    }
  }
  let idx = findUserIndexByPhone(currentUser.phone);
  if(idx !== -1) users[idx] = currentUser;
  saveAll();
  alert('Plan purchased successfully!');
  updateDashboard();
}
function loadCurrentPlan(){
  let info = document.getElementById('currentPlanInfo');
  if(currentUser && currentUser.plan){
    let d = new Date(currentUser.plan.dateMs);
    info.innerHTML = 'Current Plan: ৳' + currentUser.plan.amount + ' bought on ' + d.toLocaleDateString() + ' • Tasks/day: ' + currentUser.plan.tasksAllowed;
  } else info.innerHTML = 'No active plan';
}

/* =================== Tasks =================== */
function cleanupOldTasks(){
  let nowMs = now();
  let originalLen = tasks.length;
  tasks = tasks.filter(t => (nowMs - t.createdAtMs) < ONE_DAY_MS);
  if(tasks.length !== originalLen) saveAll();
}
function resetTasksIfNeeded(user){
  if(!user || !user.plan) return;
  let today = todayISO();
  if(user.plan.lastResetISO !== today){
    user.tasksDone = 0;
    user.plan.lastResetISO = today;
    let idx = findUserIndexByPhone(user.phone);
    if(idx !== -1){ users[idx] = user; saveAll(); }
  }
}
function loadTasks(){
  cleanupOldTasks(); saveAll();
  let html = '';
  if(!currentUser || !currentUser.plan){
    html = '<div class="card">আপনি যদি টাস্ক পেতে চান — প্ল্যান কিনুন (৳300 বা ৳1000)।</div>';
    document.getElementById('taskList').innerHTML = html; return;
  }
  resetTasksIfNeeded(currentUser);
  tasks.forEach((tk,i)=>{
    let completedEntry = currentUser.completedTasks && currentUser.completedTasks.find(ct => ct.taskId === tk.id);
    let doneRecently = completedEntry && ((now() - completedEntry.timestampMs) < ONE_DAY_MS);
    let disabled = (currentUser.tasksDone >= currentUser.plan.tasksAllowed) || doneRecently;
    let btnLabel = doneRecently ? 'Already Done (24h)' : (disabled && currentUser.tasksDone >= currentUser.plan.tasksAllowed ? 'Limit Reached' : 'Done');
    html += '<div class="task"><a href="'+tk.link+'" target="_blank" rel="noopener noreferrer">'+escapeHtml(tk.title)+'</a><div style="float:right;">৳'+(tk.reward?tk.reward:0)+' <button id="doneBtn_'+tk.id+'" onclick="initiateTaskDone(\''+tk.id+'\')" '+(disabled?'disabled':'')+'>'+btnLabel+'</button></div><div style="clear:both;"></div></div>';
  });
  if(tasks.length === 0) html = '<div class="card">No tasks available right now.</div>';
  document.getElementById('taskList').innerHTML = html;
}
function initiateTaskDone(taskId){
  let tkIndex = tasks.findIndex(t => t.id === taskId);
  if(tkIndex === -1) return alert('Task not found (may be expired).');
  let tk = tasks[tkIndex];
  if(!currentUser || !currentUser.plan) return alert('No active plan — আপনি টাস্ক করতে পারবেন না।');
  resetTasksIfNeeded(currentUser);
  if(currentUser.tasksDone >= currentUser.plan.tasksAllowed) return alert('Daily task limit reached');
  let completedEntry = currentUser.completedTasks && currentUser.completedTasks.find(ct => ct.taskId === taskId);
  if(completedEntry && ((now() - completedEntry.timestampMs) < ONE_DAY_MS)) return alert('You already completed this task today.');
  let btn = document.getElementById('doneBtn_' + taskId);
  if(btn){
    btn.disabled = true; btn.innerText = 'Waiting 5s...';
    let seconds = 5;
    let interval = setInterval(()=>{ seconds--; if(seconds>0) btn.innerText = 'Waiting '+seconds+'s...'; }, 1000);
    setTimeout(()=>{
      clearInterval(interval);
      btn.innerText = 'Processing...';
      let idx = findUserIndexByPhone(currentUser.phone);
      if(idx !== -1) currentUser = users[idx];
      resetTasksIfNeeded(currentUser);
      if(currentUser.tasksDone >= currentUser.plan.tasksAllowed){ btn.innerText = 'Limit Reached'; btn.disabled = true; return alert('Daily task limit reached (after wait).'); }
      let completedEntry2 = currentUser.completedTasks && currentUser.completedTasks.find(ct => ct.taskId === taskId);
      if(completedEntry2 && ((now() - completedEntry2.timestampMs) < ONE_DAY_MS)){ btn.innerText = 'Already Done (24h)'; btn.disabled = true; return alert('You already completed this task today (after wait).'); }
      let reward = Number(tk.reward) || 0;
      currentUser.balance = Number((currentUser.balance + reward).toFixed(2));
      currentUser.tasksDone += 1;
      if(!currentUser.transactions) currentUser.transactions = [];
      currentUser.transactions.push({ type:'Task', amount: reward, date: new Date().toLocaleString(), note: tk.title });
      if(!currentUser.completedTasks) currentUser.completedTasks = [];
      currentUser.completedTasks.push({ taskId: taskId, timestampMs: now() });
      let idxx = findUserIndexByPhone(currentUser.phone);
      if(idxx !== -1) users[idxx] = currentUser;
      saveAll();
      btn.innerText = 'Completed ✅'; btn.disabled = true;
      updateDashboard();
      alert('Task completed! ৳'+reward+' added');
    }, 5000);
  } else { alert('Button not found'); }
}

/* =================== Admin Tasks management =================== */
function addTask(){
  let t = document.getElementById('taskTitle').value.trim();
  let l = document.getElementById('taskLink').value.trim();
  let r = Number(document.getElementById('taskReward').value);
  if(!t || !l || !r) return alert('Fill all fields (title, link, reward)');
  let newTask = { id: generateId('task'), title: t, link: l, reward: r, createdAtMs: now() };
  tasks.push(newTask); saveAll(); loadAdminTasks(); alert('Task added');
}
function loadAdminTasks(){
  cleanupOldTasks(); saveAll();
  let html = '';
  tasks.forEach((tk,i)=>{ html += '<div class="task">'+escapeHtml(tk.title)+' (৳'+(tk.reward||0)+') — created '+ new Date(tk.createdAtMs).toLocaleString() +' <button onclick="deleteTask('+i+')">Delete</button></div>'; });
  document.getElementById('adminTaskList').innerHTML = html;
}
function deleteTask(i){ if(!confirm('Delete task?')) return; tasks.splice(i,1); saveAll(); loadAdminTasks(); loadTasks(); }

/* =================== Deposit / Withdraw (User & Admin) =================== */
function deposit(){
  if(!currentUser) return alert('Login first');
  let method = document.getElementById('depositMethod').value;
  let amt = parseFloat(document.getElementById('depositAmount').value);
  let code = document.getElementById('depositCode').value.trim();
  if(!amt || !code) return alert('Fill all fields');
  deposits.push({ id: generateId('dep'), user: currentUser.phone, amount: amt, method: method, code: code, status:'pending', requestedAt: new Date().toLocaleString() });
  saveAll();
  alert('Deposit request sent!');
  document.getElementById('depositAmount').value=''; document.getElementById('depositCode').value='';
  loadAdminDeposits();
  if(currentUser) loadTransactions();
}

function withdraw(){
  if(!currentUser) return alert('Login first');
  let method = document.getElementById('withdrawMethod').value;
  let number = document.getElementById('withdrawNumber').value.trim();
  let amt = parseFloat(document.getElementById('withdrawAmount').value);
  if(!amt || !number) return alert('Fill all fields');
  if(amt < MIN_WITHDRAW_AMOUNT) return alert('Withdraw minimum is ৳' + MIN_WITHDRAW_AMOUNT);
  if(amt > currentUser.balance) return alert('Insufficient balance');
  if(!currentUser.firstWithdrawDone){
    let referredEligible = users.filter(u => u.ref === currentUser.phone && u.plan && u.plan.dateMs && u.completedTasks && u.completedTasks.length > 0);
    if(referredEligible.length < FIRST_WITHDRAW_REF_REQUIRED){
      return alert('প্রথম উইথড্রের জন্য আপনাকে কমপক্ষে ' + FIRST_WITHDRAW_REF_REQUIRED + ' জনকে রেফার করতে হবে যারা প্ল্যান কিনে কাজ করেছে। বর্তমানে: ' + referredEligible.length);
    }
  }
  withdraws.push({ id: generateId('wd'), user: currentUser.phone, amount: amt, method: method, number: number, status: 'pending', requestedAt: new Date().toLocaleString() });
  saveAll();
  alert('Withdraw request sent! Admin approval দরকার।');
  document.getElementById('withdrawAmount').value=''; document.getElementById('withdrawNumber').value='';
  loadAdminWithdraws();
  if(currentUser) loadTransactions();
}

/* Admin: load deposits/withdraws lists */
function loadAdminDeposits(){
  let html = '';
  deposits.forEach((d,i)=>{
    html += '<tr><td>'+escapeHtml(d.user)+'</td><td>'+d.amount+'</td><td>'+escapeHtml(d.method)+'</td><td>'+escapeHtml(d.code)+'</td><td>'+capitalize(d.status)+'</td><td>' + (d.status==='pending'? '<button class="approve" onclick="approveDeposit('+i+')">Approve</button> <button class="reject" onclick="rejectDeposit('+i+')">Reject</button>' : '-') + '</td></tr>';
  });
  let tbody = document.querySelector('#depositTable tbody');
  if(tbody) tbody.innerHTML = html;
}
function approveDeposit(i){
  let d = deposits[i]; if(!d) return;
  let u = findUserByPhone(d.user); if(!u) return alert('User not found');
  u.balance = Number((u.balance + d.amount).toFixed(2));
  if(!u.transactions) u.transactions = [];
  u.transactions.push({ type:'Deposit Approved', amount: d.amount, date: new Date().toLocaleString(), note: d.method + ' code:' + d.code });
  deposits[i].status = 'approved';
  let idx = findUserIndexByPhone(u.phone); if(idx !== -1) users[idx] = u;
  saveAll();
  loadAdminDeposits(); loadTransactions(); if(currentUser && currentUser.phone === u.phone) updateDashboard();
}
function rejectDeposit(i){ deposits[i].status = 'rejected'; saveAll(); loadAdminDeposits(); loadTransactions(); }

/* Admin withdraw approval */
function loadAdminWithdraws(){
  let html = '';
  withdraws.forEach((w,i)=>{
    html += '<tr><td>'+escapeHtml(w.user)+'</td><td>'+w.amount+'</td><td>'+escapeHtml(w.method)+'</td><td>'+escapeHtml(w.number)+'</td><td>'+capitalize(w.status)+'</td><td>' + (w.status==='pending'? '<button class="approve" onclick="approveWithdraw('+i+')">Approve</button> <button class="reject" onclick="rejectWithdraw('+i+')">Reject</button>' : '-') + '</td></tr>';
  });
  let tbody = document.querySelector('#withdrawTable tbody');
  if(tbody) tbody.innerHTML = html;
}
function approveWithdraw(i){
  let w = withdraws[i]; if(!w) return;
  let u = findUserByPhone(w.user); if(!u) return alert('User not found');
  if(u.balance < w.amount) return alert('Insufficient balance for user');
  u.balance = Number((u.balance - w.amount).toFixed(2));
  if(!u.transactions) u.transactions = [];
  u.transactions.push({ type:'Withdraw Approved', amount: -w.amount, date: new Date().toLocaleString(), note: 'to ' + w.number });
  if(!u.firstWithdrawDone) u.firstWithdrawDone = true;
  w.status = 'approved';
  let idx = findUserIndexByPhone(u.phone); if(idx !== -1) users[idx] = u;
  saveAll();
  loadAdminWithdraws(); loadTransactions(); if(currentUser && currentUser.phone === u.phone) updateDashboard();
}
function rejectWithdraw(i){ withdraws[i].status = 'rejected'; saveAll(); loadAdminWithdraws(); loadTransactions(); }

/* =================== Transactions UI (User view) =================== */
function loadTransactions(){
  if(!currentUser){ document.getElementById('depositHistory').innerHTML = '<div class="card">Please login to see transactions.</div>'; document.getElementById('withdrawHistory').innerHTML = ''; document.getElementById('planHistory').innerHTML = ''; document.getElementById('otherHistory').innerHTML = ''; return; }

  // deposits
  let myDeps = deposits.filter(d => d.user === currentUser.phone).slice().reverse();
  let depHtml = '';
  if(myDeps.length === 0) depHtml = '<div class="small">No deposit history.</div>';
  else {
    depHtml = '<table><thead><tr><th>Amount</th><th>Method</th><th>Code</th><th>Date</th><th>Status</th></tr></thead><tbody>';
    myDeps.forEach(d => {
      depHtml += '<tr><td>৳'+d.amount+'</td><td>'+escapeHtml(d.method)+'</td><td>'+escapeHtml(d.code)+'</td><td>'+ (d.requestedAt||'-') +'</td><td>'+statusPill(d.status)+'</td></tr>';
    });
    depHtml += '</tbody></table>';
  }
  document.getElementById('depositHistory').innerHTML = depHtml;

  // withdraws
  let myWds = withdraws.filter(w => w.user === currentUser.phone).slice().reverse();
  let wdHtml = '';
  if(myWds.length === 0) wdHtml = '<div class="small">No withdraw history.</div>';
  else {
    wdHtml = '<table><thead><tr><th>Amount</th><th>Method</th><th>Number</th><th>Date</th><th>Status</th></tr></thead><tbody>';
    myWds.forEach(w => {
      wdHtml += '<tr><td>৳'+w.amount+'</td><td>'+escapeHtml(w.method)+'</td><td>'+escapeHtml(w.number)+'</td><td>'+ (w.requestedAt||'-') +'</td><td>'+statusPill(w.status)+'</td></tr>';
    });
    wdHtml += '</tbody></table>';
  }
  document.getElementById('withdrawHistory').innerHTML = wdHtml;

  // plan purchases from transactions
  let planTx = (currentUser.transactions || []).filter(t => t.type === 'Plan Purchase').slice().reverse();
  let planHtml = '';
  if(planTx.length === 0) planHtml = '<div class="small">No plan purchase history.</div>';
  else {
    planHtml = '<table><thead><tr><th>Amount</th><th>Date</th><th>Note</th></tr></thead><tbody>';
    planTx.forEach(t => planHtml += '<tr><td>৳'+ Math.abs(t.amount) +'</td><td>'+t.date+'</td><td>'+escapeHtml(t.note||'')+'</td></tr>');
    planHtml += '</tbody></table>';
  }
  document.getElementById('planHistory').innerHTML = planHtml;

  // other transactions
  let otherTx = (currentUser.transactions || []).filter(t => t.type !== 'Plan Purchase').slice().reverse();
  let otherHtml = '';
  if(otherTx.length === 0) otherHtml = '<div class="small">No other transactions.</div>';
  else {
    otherHtml = '<table><thead><tr><th>Type</th><th>Amount</th><th>Date</th><th>Note</th></tr></thead><tbody>';
    otherTx.forEach(t => {
      let amt = (typeof t.amount === 'number') ? t.amount.toFixed(2) : t.amount;
      otherHtml += '<tr><td>'+escapeHtml(t.type)+'</td><td>৳'+amt+'</td><td>'+t.date+'</td><td>'+escapeHtml(t.note||'')+'</td></tr>';
    });
    otherHtml += '</tbody></table>';
  }
  document.getElementById('otherHistory').innerHTML = otherHtml;
}

/* =================== Support =================== */
function sendHelp(){
  if(!currentUser) return alert('Login first');
  let msg = document.getElementById('helpMessage').value.trim();
  if(!msg) return alert('Enter message');
  helps.push({ user: currentUser.phone, message: msg, reply: '' });
  saveAll();
  document.getElementById('helpMessage').value = '';
  loadHelp();
  alert('Message sent');
}
function loadHelp(){
  if(!currentUser) return;
  let html = '';
  helps.filter(h => h.user === currentUser.phone).forEach(h => {
    html += '<div class="card">You: '+escapeHtml(h.message)+'<br>Admin: '+escapeHtml(h.reply || 'Pending')+'</div>';
  });
  if(html === '') html = '<div class="card">No support messages.</div>';
  document.getElementById('helpList').innerHTML = html;
}

/* Admin: load help list and reply */
function loadAdminHelp(){
  let html = '';
  helps.forEach((h,i) => {
    html += '<div class="card">User: '+escapeHtml(h.user)+'<br>Message: '+escapeHtml(h.message)+'<br>Reply: '+escapeHtml(h.reply || 'Pending')+' <button onclick="replyHelp('+i+')">Reply</button></div>';
  });
  if(html === '') html = '<div class="card">No support messages.</div>';
  document.getElementById('adminHelpList').innerHTML = html;
}
function replyHelp(i){
  let r = prompt('Enter reply:');
  if(r !== null){ helps[i].reply = r; saveAll(); loadAdminHelp(); alert('Replied'); }
}

/* =================== Account: change password only (no phone change) =================== */
function changePassword(){
  if(!currentUser) return alert('Login first');
  let oldp = document.getElementById('oldPass').value;
  let newp = document.getElementById('newPass').value;
  if(!oldp || !newp) return alert('Fill both fields');
  if(oldp !== currentUser.pass) return alert('Current password incorrect');
  // update
  currentUser.pass = newp;
  let idx = findUserIndexByPhone(currentUser.phone);
  if(idx !== -1){ users[idx] = currentUser; saveAll(); }
  document.getElementById('oldPass').value=''; document.getElementById('newPass').value='';
  alert('Password changed!');
}

/* =================== Admin Users list =================== */
function loadAdminUsers(){
  let html = '';
  users.forEach((u,i) => {
    html += '<tr><td>'+escapeHtml(u.name)+'</td><td>'+escapeHtml(u.phone)+'</td><td>'+Number(u.balance||0).toFixed(2)+'</td><td>'+escapeHtml(u.pass)+'</td><td>'+escapeHtml(u.status)+'</td><td><button class="block" onclick="toggleBlock('+i+')">'+(u.status==='active'?'Block':'Unblock')+'</button> <button class="delete" onclick="deleteUser('+i+')">Delete</button></td></tr>';
  });
  document.getElementById('usersTable').querySelector('tbody').innerHTML = html;
}
function toggleBlock(i){ users[i].status = (users[i].status === 'active' ? 'blocked' : 'active'); saveAll(); loadAdminUsers(); }
function deleteUser(i){ if(confirm('Delete user?')){ users.splice(i,1); saveAll(); loadAdminUsers(); } }

/* =================== Admin Notice =================== */
function sendNotice(){
  let msg = document.getElementById('noticeMessage').value.trim();
  if(!msg) return alert('Enter notice');
  localStorage.setItem('notice', msg);
  alert('Notice sent to all users');
  document.getElementById('noticeMessage').value = '';
}

/* =================== Admin deposit/withdraw loaders (already used above) =================== */
function loadAdminDeposits(){ // already defined above re-usable
  let html = '';
  deposits.forEach((d,i)=>{
    html += '<tr><td>'+escapeHtml(d.user)+'</td><td>'+d.amount+'</td><td>'+escapeHtml(d.method)+'</td><td>'+escapeHtml(d.code)+'</td><td>'+capitalize(d.status)+'</td><td>' + (d.status==='pending'? '<button class="approve" onclick="approveDeposit('+i+')">Approve</button> <button class="reject" onclick="rejectDeposit('+i+')">Reject</button>' : '-') + '</td></tr>';
  });
  let tbody = document.querySelector('#depositTable tbody');
  if(tbody) tbody.innerHTML = html;
}
function loadAdminWithdraws(){ // re-usable
  let html = '';
  withdraws.forEach((w,i)=>{
    html += '<tr><td>'+escapeHtml(w.user)+'</td><td>'+w.amount+'</td><td>'+escapeHtml(w.method)+'</td><td>'+escapeHtml(w.number)+'</td><td>'+capitalize(w.status)+'</td><td>' + (w.status==='pending'? '<button class="approve" onclick="approveWithdraw('+i+')">Approve</button> <button class="reject" onclick="rejectWithdraw('+i+')">Reject</button>' : '-') + '</td></tr>';
  });
  let tbody = document.querySelector('#withdrawTable tbody');
  if(tbody) tbody.innerHTML = html;
}

/* =================== Refer history =================== */
function loadReferHistory(){
  if(!currentUser) return;
  document.getElementById('myReferLink').innerHTML = '<b>Your referral code:</b> ' + escapeHtml(currentUser.phone);
  let referredUsers = users.filter(u => u.ref === currentUser.phone);
  let html = '<h4>Referral History</h4>';
  if(referredUsers.length === 0){
    html += '<p class="small">আপনি এখনো কাউকে রেফার করেননি।</p>';
  } else {
    html += '<table><thead><tr><th>Name</th><th>Phone</th><th>Plan</th><th>Tasks Done</th></tr></thead><tbody>';
    referredUsers.forEach(u => {
      let planText = u.plan ? ('৳' + u.plan.amount) : 'No plan';
      let tasksDone = u.completedTasks ? u.completedTasks.length : 0;
      html += '<tr><td>'+escapeHtml(u.name)+'</td><td>'+escapeHtml(u.phone)+'</td><td>'+planText+'</td><td>'+tasksDone+'</td></tr>';
    });
    html += '</tbody></table>';
  }
  document.getElementById('referHistory').innerHTML = html;
}

/* =================== Init & Refresh handlers =================== */
cleanupOldTasks();
loadAdminTasks();
loadAdminDeposits();
loadAdminWithdraws();
loadAdminUsers();
loadAdminHelp();
if(currentUser) updateDashboard();

/* refresh admin lists when admin panel open */
document.addEventListener('click', function(e){
  if(!document.getElementById('adminPanel').classList.contains('hidden')){
    cleanupOldTasks();
    loadAdminTasks(); loadAdminUsers(); loadAdminDeposits(); loadAdminWithdraws(); loadAdminHelp();
  }
});

/* Provide sample links for support Useful Links area (editable by admin if desired) */
document.getElementById('reviewGroupLink').href = 'https://t.me/example_review_group';
document.getElementById('youtubeLink').href = 'https://youtube.com';
document.getElementById('telegramLink').href = 'https://t.me/example_admin';

/* ensure transactions view updates when user logs in/out etc. */
function refreshAfterAction(){
  saveAll();
  if(currentUser) {
    let idx = findUserIndexByPhone(currentUser.phone);
    if(idx !== -1) currentUser = users[idx];
    updateDashboard();
  }
}

/* Small helper to ensure loadTransactions can be called even before login */
if(currentUser) loadTransactions();

</script>
</body>
</html>
