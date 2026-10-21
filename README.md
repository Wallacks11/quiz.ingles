[index.html](https://github.com/user-attachments/files/33792147/index_novo.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#0b0e0c">
<title>A Vila | Central de Quizzes</title>
<style>
:root{--bg:#090c0a;--panel:#141a16;--panel2:#1b221d;--text:#f3f1e8;--muted:#a8b0a8;--gold:#d7bd7b;--line:#303a32}
*{box-sizing:border-box}html{scroll-behavior:smooth}
body{margin:0;background:var(--bg);color:var(--text);font-family:Arial,sans-serif}
nav{position:absolute;top:0;left:0;right:0;z-index:5;padding:24px 6vw;display:flex;justify-content:space-between;align-items:center}
.logo{font:24px Georgia,serif}.nav-links{display:flex;gap:24px}.nav-links button{background:none;border:0;color:#ddd;cursor:pointer;font-size:12px;letter-spacing:.08em}
.hero{min-height:88vh;display:flex;align-items:center;justify-content:center;text-align:center;position:relative;overflow:hidden;
background:linear-gradient(rgba(5,8,6,.48),rgba(5,8,6,.88)),url('https://images.unsplash.com/photo-1448375240586-882707db888b?auto=format&fit=crop&w=2000&q=90') center/cover}
.hero:after{content:"";position:absolute;bottom:0;left:0;right:0;height:160px;background:linear-gradient(transparent,var(--bg))}
.hero-content{position:relative;z-index:2;padding:30px}
.kicker{font-size:11px;color:var(--gold);letter-spacing:.3em;text-transform:uppercase}
.hero h1{font:normal clamp(5rem,13vw,10rem) Georgia,serif;line-height:.8;margin:25px 0}
.hero h1 span{color:var(--gold);font-style:italic}
.hero p{max-width:600px;margin:0 auto 25px;color:#e1e5df;line-height:1.7;font-size:15px}
.btn{border:1px solid var(--gold);background:var(--gold);color:#14150f;padding:13px 20px;font-size:11px;font-weight:bold;letter-spacing:.12em;text-transform:uppercase;cursor:pointer}
.btn:hover{background:transparent;color:var(--gold)}.btn.secondary{background:transparent;color:var(--gold)}
main{max-width:1200px;margin:auto;padding:70px 24px}
.heading{display:flex;justify-content:space-between;align-items:end;gap:25px;margin-bottom:28px}
.heading h2{font:normal clamp(2rem,5vw,3.3rem) Georgia,serif;margin:0}
.heading p{max-width:420px;color:var(--muted);font-size:13px;line-height:1.6}
.grid{display:grid;grid-template-columns:repeat(4,1fr);gap:15px}
.card{height:310px;position:relative;overflow:hidden;border:1px solid var(--line);cursor:pointer;background:var(--panel)}
.card img{position:absolute;width:100%;height:100%;object-fit:cover;inset:0;filter:saturate(.6);transition:.5s}
.card:hover img{transform:scale(1.07);filter:saturate(.9)}
.card:after{content:"";position:absolute;inset:0;background:linear-gradient(transparent 20%,rgba(5,8,6,.95))}
.card-content{position:absolute;z-index:2;bottom:0;padding:20px}.number{color:var(--gold);font-size:10px;letter-spacing:.2em}
.card h3{font:normal 22px Georgia,serif;margin:9px 0}.card p{font-size:12px;color:#c4cbc5;line-height:1.5;margin:0}
.quiz{display:none;margin-top:70px;border:1px solid var(--line);background:linear-gradient(145deg,var(--panel2),var(--panel));padding:30px}
.quiz.active{display:block}.quiz-head{display:flex;justify-content:space-between;gap:15px;align-items:center}
.quiz-head h2{font:normal 30px Georgia,serif;margin:0}.counter{font-size:12px;color:var(--gold)}
.progress{height:3px;background:#333c34;margin:25px 0}.progress span{display:block;height:100%;width:0;background:var(--gold)}
.question{font:normal clamp(1.5rem,3vw,2.5rem) Georgia,serif;line-height:1.3;margin:25px 0}
.answers{display:grid;grid-template-columns:1fr 1fr;gap:11px}.answer{padding:16px;text-align:left;background:#1b221d;border:1px solid #38423a;color:white;cursor:pointer}
.answer:hover,.answer.selected{border-color:var(--gold);background:#292f27}.answer.correct{border-color:#9bb584;background:#263725}.answer.wrong{border-color:#bb7d6e;background:#39251f}
.feedback{min-height:20px;margin-top:13px;color:var(--muted);font-size:13px}.actions{display:flex;justify-content:space-between;margin-top:22px}
.leaderboard{margin-top:75px}.table{border:1px solid var(--line);background:var(--panel)}
.row{display:grid;grid-template-columns:60px 1fr 100px 180px;padding:16px 18px;border-bottom:1px solid var(--line);align-items:center;gap:10px}
.row:last-child{border:0}.row.head{color:var(--muted);font-size:10px;letter-spacing:.1em;text-transform:uppercase}.rank{color:var(--gold);font-weight:bold}
.auth{display:none;position:fixed;z-index:20;inset:0;background:rgba(0,0,0,.78);align-items:center;justify-content:center;padding:20px}.auth.active{display:flex}
.auth-box{width:min(420px,100%);background:#111613;border:1px solid var(--line);padding:30px}.auth-box h2{font:normal 30px Georgia,serif;margin-top:0}
.auth-box p{color:var(--muted);font-size:13px;line-height:1.5}.auth-box input{display:block;width:100%;margin:8px 0;padding:13px;background:#090c0a;border:1px solid #364039;color:white}
.auth-actions{display:flex;gap:10px;margin-top:13px}.auth-msg{font-size:12px;color:var(--muted);margin-top:12px;min-height:18px}
footer{border-top:1px solid var(--line);padding:28px;text-align:center;color:#737d75;font-size:11px;letter-spacing:.1em}
@media(max-width:900px){.grid{grid-template-columns:repeat(2,1fr)}}
@media(max-width:600px){.nav-links{display:none}.hero h1{font-size:clamp(4rem,20vw,7rem)}.grid{grid-template-columns:1fr 1fr;gap:9px}.card{height:260px}.answers{grid-template-columns:1fr}.quiz{padding:18px}.row{grid-template-columns:45px 1fr 75px}.row div:last-child{display:none}.heading{display:block}}
</style>
</head>
<body>

<nav>
  <div class="logo">A VILA</div>
  <div class="nav-links">
    <button onclick="go('quizzes')">QUIZZES</button>
    <button onclick="go('ranking')">RANKING</button>
    <button onclick="openAuth()">CRIAR CONTA</button>
  </div>
</nav>

<header class="hero">
  <div class="hero-content">
    <div class="kicker">Uma experiência interativa</div>
    <h1>A <span>Vila</span></h1>
    <p>Entre na comunidade, teste seus conhecimentos e descubra sua posição entre os jogadores.</p>
    <button class="btn" onclick="play()">Começar a jogar</button>
  </div>
</header>

<main>
<section id="quizzes">
  <div class="heading">
    <h2>Escolha seu desafio</h2>
    <p>As perguntas dos desafios estão em inglês. Crie uma conta para salvar seus resultados e participar do ranking.</p>
  </div>
  <div class="grid" id="cards"></div>
</section>

<section class="quiz" id="quiz">
  <div class="quiz-head"><h2 id="quizTitle">Quiz</h2><div class="counter" id="counter"></div></div>
  <div class="progress"><span id="progress"></span></div>
  <div class="question" id="question"></div>
  <div class="answers" id="answers"></div>
  <div class="feedback" id="feedback"></div>
  <div class="actions">
    <button class="btn secondary" onclick="closeQuiz()">← Voltar</button>
    <button class="btn" id="next" onclick="next()">Responder</button>
  </div>
</section>

<section class="leaderboard" id="ranking">
  <div class="heading">
    <h2>Ranking da Vila</h2>
    <p>Veja os jogadores que já fizeram os desafios e suas melhores pontuações neste navegador.</p>
  </div>
  <div class="table">
    <div class="row head"><div>#</div><div>Jogador</div><div>Pontos</div><div>Desafio</div></div>
    <div id="rows"></div>
  </div>
</section>
</main>

<div class="auth" id="auth">
<div class="auth-box">
  <h2>Criar sua conta</h2>
  <p>Crie seu perfil para poder jogar e registrar sua pontuação no ranking.</p>
  <input id="name" placeholder="Nome de usuário">
  <input id="email" type="email" placeholder="E-mail">
  <input id="password" type="password" placeholder="Senha">
  <div class="auth-actions">
    <button class="btn" onclick="createAccount()">Criar conta</button>
    <button class="btn secondary" onclick="closeAuth()">Fechar</button>
  </div>
  <div class="auth-msg" id="authMsg"></div>
</div>
</div>

<footer>A VILA · CENTRAL DE QUIZZES · EXPERIÊNCIA NÃO OFICIAL</footer>

<script>
const quizzes=[
{title:"Você realmente entendeu A Vila?",desc:"Acontecimentos e personagens",img:"https://images.unsplash.com/photo-1511497584788-876760111969?auto=format&fit=crop&w=800&q=85",qs:[
["What kind of place does the community live in?",["An isolated village","A large city","A tourist island","Underground"],0],
["What do the villagers fear is in the forest?",["Ordinary animals","Mysterious creatures","Armies","Storms"],1],
["Who is the blind character at the center of the story?",["Kitty","Alice","Ivy Walker","Tabitha"],2],
["What is the main purpose of the community's rules?",["To organize parties","To keep everyone within the imposed boundaries","To teach farming","To choose occupations"],1],
["Who are the Elders?",["Visitors","The community's older leaders","Forest guards","Village children"],1]]},
{title:"Você descobriria o segredo?",desc:"Leia as pistas e desconfie",img:"https://images.unsplash.com/photo-1448375240586-882707db888b?auto=format&fit=crop&w=800&q=85",qs:[
["The stories about the creatures are presented as…",["An unimportant legend","A threat that shapes local life","A children's game","A festival"],1],
["The village's isolation is…",["Central to the mystery","Unrelated to the plot","Only decorative","Only shown at the end"],0],
["How should viewers respond to the Elders' explanations?",["Accept them without question","Look for inconsistencies and clues","Ignore the characters","Assume it is all a dream"],1]]},
{title:"Quem disse isso?",desc:"Associe ideias aos personagens",img:"https://images.unsplash.com/photo-1518709268805-4e9042af9f23?auto=format&fit=crop&w=800&q=85",qs:[
["Who is the young woman who wants to help Lucius?",["Ivy Walker","Kitty","Mrs. Clack","Tabitha"],0],
["Who holds a leadership position among the Elders?",["Lucius","The Elders","Noah","The children"],1]]},
{title:"Realidade ou mentira?",desc:"As regras e as versões da vila",img:"https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=800&q=85",qs:[
["The villagers avoid entering the forest because they fear the creatures.",["True","False"],0],
["The village maintains regular, open contact with large cities.",["True","False"],1],
["The Elders control important information about the community.",["True","False"],0]]},
{title:"O que você faria na Vila?",desc:"Escolhas em situações fictícias",img:"https://images.unsplash.com/photo-1441974231531-c6227db76b6e?auto=format&fit=crop&w=800&q=85",qs:[
["You hear a strange noise coming from the forest. What do you do?",["Find a trusted adult and follow the rules","Go in alone to investigate","Pretend nothing happened","Convince everyone to come with you"],0],
["Someone questions an old rule. How do you react?",["Listen and try to understand why","Spread rumors","Threaten the person","Decide without listening to anyone"],0]]},
{title:"Teste de memória",desc:"Detalhes que podem passar despercebidos",img:"https://images.unsplash.com/photo-1470770841072-f978cf4d019e?auto=format&fit=crop&w=800&q=85",qs:[
["Which of Ivy's senses is especially important to the story?",["Hearing","Smell","Sight","Touch"],2],
["What is the name of the young man Ivy has feelings for?",["Lucius Hunt","Noah Percy","Edward Walker","August Nicholson"],0]]},
{title:"Quiz sem spoilers",desc:"A premissa e a atmosfera",img:"https://images.unsplash.com/photo-1473448912268-2022ce9509d8?auto=format&fit=crop&w=800&q=85",qs:[
["What is the community like at the beginning of the story?",["Isolated and rural","A metropolis","A space station","A ship"],0],
["What atmosphere dominates the film?",["Fast-paced comedy","Mystery and suspense","Musical","Space adventure"],1],
["Who is at the center of an important part of the story?",["Ivy Walker","A city detective","An astronaut","A king"],0]]},
{title:"Quiz com spoilers",desc:"Revelações e desfecho",img:"https://images.unsplash.com/photo-1511497584788-876760111969?auto=format&fit=crop&w=800&q=85",qs:[
["What is revealed about the creatures?",["They are real supernatural beings","The threat is staged by the villagers themselves","They are animals from another planet","They are only Ivy's hallucinations"],1],
["In what era is the outside world actually living?",["18th century","19th century","Contemporary times","Distant future"],2],
["Why did the Elders create the isolated community?",["To protect the community from the outside world after traumatic experiences","To mine for resources","To hide a treasure","To train soldiers"],0]]}
];

let current=0,index=0,score=0,selected=null,answered=false;
const $=id=>document.getElementById(id);
function go(id){$(id).scrollIntoView({behavior:"smooth"})}
function user(){return JSON.parse(localStorage.getItem("aVilaUser")||"null")}
function openAuth(){$("auth").classList.add("active")}
function closeAuth(){$("auth").classList.remove("active")}
function createAccount(){
 const name=$("name").value.trim(),email=$("email").value.trim(),password=$("password").value;
 if(name.length<2||!email||password.length<4){$("authMsg").textContent="Preencha todos os campos. A senha precisa ter pelo menos 4 caracteres.";return}
 localStorage.setItem("aVilaUser",JSON.stringify({name,email}));
 $("authMsg").textContent="Conta criada!";
 setTimeout(()=>{closeAuth();go("quizzes")},400);
}
function play(){if(!user())openAuth();else go("quizzes")}
function renderCards(){
 quizzes.forEach((q,i)=>{
  const c=document.createElement("article");c.className="card";
  c.innerHTML=`<img src="${q.img}" alt=""><div class="card-content"><div class="number">DESAFIO 0${i+1}</div><h3>${q.title}</h3><p>${q.desc}</p></div>`;
  c.onclick=()=>start(i);$("cards").appendChild(c);
 });
}
function start(i){
 if(!user()){openAuth();return}
 current=i;index=0;score=0;show();
 $("quiz").classList.add("active");$("quiz").scrollIntoView({behavior:"smooth",block:"start"});
}
function show(){
 const q=quizzes[current],item=q.qs[index];selected=null;answered=false;
 $("quizTitle").textContent=q.title;$("counter").textContent=`${index+1} / ${q.qs.length}`;
 $("progress").style.width=(index/q.qs.length*100)+"%";$("question").textContent=item[0];
 $("answers").innerHTML="";$("feedback").textContent="";$("next").textContent="Responder";
 item[1].forEach((answer,i)=>{
  const b=document.createElement("button");b.className="answer";b.textContent=String.fromCharCode(65+i)+". "+answer;
  b.onclick=()=>{if(answered)return;selected=i;document.querySelectorAll(".answer").forEach(x=>x.classList.remove("selected"));b.classList.add("selected")};
  $("answers").appendChild(b);
 });
}
function next(){
 const item=quizzes[current].qs[index];
 if(!answered){
  if(selected===null){$("feedback").textContent="Escolha uma resposta primeiro.";return}
  answered=true;
  [...document.querySelectorAll(".answer")].forEach((b,i)=>{b.disabled=true;if(i===item[2])b.classList.add("correct");if(i===selected&&i!==item[2])b.classList.add("wrong")});
  if(selected===item[2]){score++;$("feedback").textContent="Resposta correta!"}else $("feedback").textContent="A resposta correta está destacada.";
  $("next").textContent=index===quizzes[current].qs.length-1?"Ver resultado":"Próxima";
  $("progress").style.width=((index+1)/quizzes[current].qs.length*100)+"%";return;
 }
 if(index<quizzes[current].qs.length-1){index++;show()}else finish();
}
function finish(){
 const u=user(),total=quizzes[current].qs.length;
 let scores=JSON.parse(localStorage.getItem("aVilaScores")||"[]");
 scores.push({name:u.name,score,total,quiz:quizzes[current].title,date:Date.now()});
 localStorage.setItem("aVilaScores",JSON.stringify(scores));
 $("question").textContent=`Desafio concluído! Você acertou ${score} de ${total}.`;
 $("answers").innerHTML="";$("feedback").textContent="Sua pontuação foi adicionada ao ranking.";
 $("next").textContent="Refazer";$("next").onclick=()=>{ $("next").onclick=next;start(current)};
 renderRanking();
}
function closeQuiz(){$("quiz").classList.remove("active");go("quizzes");$("next").onclick=next}
function renderRanking(){
 const box=$("rows");box.innerHTML="";
 let data=JSON.parse(localStorage.getItem("aVilaScores")||"[]").sort((a,b)=>(b.score/b.total)-(a.score/a.total)).slice(0,20);
 if(!data.length){box.innerHTML='<div class="row"><div>—</div><div>Nenhum jogador ainda</div><div>—</div><div>Seja o primeiro!</div></div>';return}
 data.forEach((p,i)=>{
  const r=document.createElement("div");r.className="row";
  r.innerHTML=`<div class="rank">${i+1}</div><div>${safe(p.name)}</div><div>${p.score}/${p.total}</div><div>${safe(p.quiz)}</div>`;
  box.appendChild(r);
 });
}
function safe(s){return String(s).replace(/[&<>"']/g,m=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#039;"}[m]))}
renderCards();renderRanking();
</script>
</body>
</html>
