# Soco-arena
Um jogo
<!doctype html><html lang="pt-BR"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"><title>SOCO ARENA — Luta e Treino</title><style>
*{box-sizing:border-box}body{margin:0;font-family:system-ui,Arial;background:#10131c;color:#fff;touch-action:pan-y}#app{min-height:100dvh;display:flex;flex-direction:column;background:radial-gradient(circle at top,#29344a,#10131c 65%)}header{padding:14px 16px;display:flex;justify-content:space-between;align-items:center;background:#080a10c9;border-bottom:1px solid #ffffff22}h1{font-size:18px;margin:0}.pill{font-size:12px;background:#26334a;padding:6px 10px;border-radius:99px}.phase-box{font-size:12px;font-weight:900;letter-spacing:.4px;background:#ffd166;color:#251a05;border:2px solid #fff0b3;padding:7px 10px;border-radius:10px;box-shadow:0 3px 0 #a66d22;white-space:nowrap}.stats{display:flex;gap:10px;padding:12px}.stat{flex:1;background:#ffffff0d;border:1px solid #ffffff18;padding:10px;border-radius:12px;text-align:center}.stat strong{display:block;font-size:20px;color:#ffd166}.arena{flex:1;min-height:290px;display:flex;align-items:center;justify-content:space-around;position:relative;overflow:hidden;background:linear-gradient(#222e43 0%,#171c2a 68%,#34303a 68%,#17151c 100%);margin:0 12px;border-radius:18px;border:1px solid #ffffff20}.arena:after{content:'';position:absolute;bottom:30%;width:100%;height:2px;background:#ffffff1c}.fighter{z-index:1;text-align:center;width:42%;}.emoji{font-size:86px;filter:drop-shadow(0 8px 5px #0008);display:block;transition:transform .15s}.fighter small{display:block;color:#d5deee;margin-top:5px}.health{height:9px;background:#512a35;border-radius:99px;overflow:hidden;margin:8px 0}.health div{height:100%;background:#ff5964;width:100%;transition:width .2s}.player .health div{background:#5be39b}.message{text-align:center;color:#d9e4f8;min-height:25px;padding:8px 10px}.controls{padding:12px;display:grid;grid-template-columns:1fr 1fr;gap:10px}.btn{border:0;border-radius:14px;padding:15px 10px;font-size:16px;font-weight:800;color:#111827;background:#ffd166;box-shadow:0 4px 0 #a66d22;cursor:pointer}.btn:active{transform:translateY(3px);box-shadow:0 1px 0 #a66d22}.btn.blue{background:#80bfff;box-shadow:0 4px 0 #3268a3}.btn.green{background:#70e6a1;box-shadow:0 4px 0 #25894d}.btn.dark{background:#343f55;color:white;box-shadow:0 4px 0 #1c2432}.hint{text-align:center;font-size:12px;color:#aebbd0;padding:0 16px 14px}.screen{display:none;flex:1;padding:14px;gap:12px;flex-direction:column}.screen.active{display:flex}.fight.active{display:flex}.fight{display:none;flex:1;flex-direction:column}.gym-title{font-size:24px;margin:4px 0}.gym-desc{color:#c0ccdf;margin:0 0 6px}.equipment{display:grid;grid-template-columns:1fr 1fr;gap:12px}.equip{border:1px solid #ffffff22;border-radius:16px;background:#ffffff0d;padding:16px 10px;text-align:center}.equip .big{font-size:42px}.equip h3{margin:5px 0;font-size:16px}.equip p{font-size:12px;color:#bdc9dc;min-height:32px;margin:5px 0 12px}.equip .btn{width:100%;font-size:14px;padding:12px 6px}.upgrade-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:2px}.progress{height:12px;background:#ffffff20;border-radius:99px;overflow:hidden}.progress div{height:100%;width:0;background:linear-gradient(90deg,#70e6a1,#ffd166);transition:width .25s}.back{margin-top:auto}.toast{background:#1c293c;border-radius:12px;padding:10px;text-align:center;color:#dce8f9}.confetti-layer{position:fixed;inset:0;pointer-events:none;overflow:hidden;z-index:99}.confetti-piece{position:absolute;top:-18px;width:9px;height:14px;animation:confettiFall linear forwards;opacity:.95}@keyframes confettiFall{to{transform:translateY(110vh) rotate(900deg);opacity:.85}}.hidden{display:none!important}
</style></head><body><div id="app"><header><h1>🥊 SOCO ARENA</h1><span class="phase-box" id="phaseBox">FASE 1</span><span class="pill" id="mode">MODO LUTA</span></header><div class="stats"><div class="stat">💥 Força<strong id="power">10</strong></div><div class="stat">🏋️ Treinos<strong id="workouts">0</strong></div><div class="stat">⭐ Nível<strong id="level">1</strong></div></div>
<section class="fight active" id="fight"><div class="arena"><div class="fighter player"><span class="emoji" id="hero">🥷</span><div>VOCÊ</div><div class="health"><div id="playerbar"></div></div><small id="playerhp">100 / 100</small></div><div class="fighter"><span class="emoji" id="enemy">🥊</span><div id="enemyname">OPONENTE #1</div><div class="health"><div id="enemybar"></div></div><small id="enemyhp">100 / 100</small></div></div><div class="message" id="msg">Desafie o oponente ou deslize para a esquerda para treinar!</div><div class="controls"><button class="btn" id="punch">👊 DAR SOCO</button><button class="btn blue" id="guard">🛡️ DEFENDER</button><button class="btn green" id="openGym">🏋️ TREINAR</button><button class="btn dark" id="reset">↻ NOVA LUTA</button></div><div class="hint">Dica: deslize para a esquerda em qualquer lugar para abrir a academia.</div></section>
<section class="screen" id="gym"><h2 class="gym-title">🏋️ Academia de Treino</h2><p class="gym-desc">Escolha um exercício para ganhar força. Cada botão dá uma quantidade diferente!</p><div class="toast" id="gymmsg">Sua força atual é <b>10</b>. Bora ficar mais forte!</div><div class="equipment"><div class="equip"><div class="big">💪</div><h3>Flexão</h3><p>Fortalece os braços: +2 de força</p><button class="btn green train" data-gain="2" data-name="Flexão">FAZER FLEXÃO</button></div><div class="equip"><div class="big">🏋️</div><h3>Levantar peso</h3><p>Treino pesado: +3 de força</p><button class="btn train" data-gain="3" data-name="Levantar peso">LEVANTAR</button></div><div class="equip"><div class="big">🤸</div><h3>Polichinelos</h3><p>Movimente o corpo: +2 de força</p><button class="btn blue train" data-gain="2" data-name="Polichinelos">FAZER POLICHINELOS</button></div><div class="equip"><div class="big">👊</div><h3>Treino de soco</h3><p>Pratique seus golpes: +1 de força</p><button class="btn dark train" data-gain="1" data-name="Treino de soco">TREINAR SOCO</button></div></div><div class="upgrade-grid"><div class="equip"><div class="big">❤️</div><h3>Regenerar</h3><p>Recupera 25 de vida e aumenta a vida máxima em 10.</p><button class="btn green" id="regenerate">REGENERAR VIDA</button></div><div class="equip"><div class="big">🛡️</div><h3>Resistência</h3><p>Deixa os socos dos oponentes mais fracos.</p><button class="btn blue" id="resistance">TREINAR RESISTÊNCIA</button></div></div><div class="upgrade-grid"><div class="equip hidden" id="ultimateTrainingCard"><div class="big">🌟</div><h3>Treino Completo</h3><p>Desbloqueado após concluir a fase 30. Fica disponível para sempre e pode ser usado quantas vezes quiser: +100 de força e +100 de vida máxima e atual.</p><button class="btn" id="ultimateTraining">TREINO COMPLETO +100</button></div></div><div class="upgrade-grid"><div class="equip hidden" id="tutorialCompleteCard"><div class="big">👑</div><h3>Tutorial Completo</h3><p>Desbloqueia na fase 100. Jogadores recebem +1.000 de força, vida máxima e resistência; o ADM pode receber +1.000.000 de cada com código ADM.</p><button class="btn" id="tutorialComplete">TUTORIAL COMPLETO</button></div></div><div><div style="display:flex;justify-content:space-between;margin:5px 0 8px"><span>Progresso do nível</span><b id="progressText">0 / 20</b></div><div class="progress"><div id="progressBar"></div></div></div><button class="btn back" id="backFight">🥊 VOLTAR PARA A LUTA</button><div class="hint">Você também pode deslizar para a direita para voltar.</div></section></div>
<script>
const $ = id => document.getElementById(id);
let power=10, workouts=0, level=1, playerMaxHP=100, playerHP=100, resistance=0;
let enemyNumber=1, enemyMaxHP=100, enemyHP=100, guarding=false, view='fight', fightStarted=false, phase30Cleared=false, tutorialCompleteUnlocked=false;
let nextEnemyTimeout=null;
const SAVE_KEY='socoArenaSaveV1';
function saveProgress(){
  try{localStorage.setItem(SAVE_KEY,JSON.stringify({power,workouts,level,playerMaxHP,playerHP,resistance,enemyNumber,enemyMaxHP,enemyHP,phase30Cleared,tutorialCompleteUnlocked}));}catch(e){}
}
function loadProgress(){
  try{const raw=localStorage.getItem(SAVE_KEY);if(!raw)return;const d=JSON.parse(raw);
    if(!d||typeof d!=='object')return;
    power=Math.max(10,Number(d.power)||10);workouts=Math.max(0,Number(d.workouts)||0);level=Math.max(1,Number(d.level)||1);
    playerMaxHP=Math.max(100,Number(d.playerMaxHP)||100);playerHP=Math.max(0,Math.min(playerMaxHP,Number.isFinite(Number(d.playerHP))?Number(d.playerHP):playerMaxHP));resistance=Math.max(0,Number(d.resistance)||0);
    enemyNumber=Math.max(1,Math.floor(Number(d.enemyNumber)||1));enemyMaxHP=Math.max(100,Number(d.enemyMaxHP)||100);enemyHP=Math.max(0,Math.min(enemyMaxHP,Number.isFinite(Number(d.enemyHP))?Number(d.enemyHP):enemyMaxHP));phase30Cleared=Boolean(d.phase30Cleared)||enemyNumber>30; tutorialCompleteUnlocked=Boolean(d.tutorialCompleteUnlocked)||enemyNumber>=100;
    fightStarted=false;
    $('enemy').textContent=['🥊','🥷','🤼','👊','🥋'][(enemyNumber-1)%5];
    if(enemyHP<=0){enemyHP=enemyMaxHP;playerHP=playerMaxHP;}
    $('msg').textContent='💾 Progresso carregado! Continue da fase '+enemyNumber+'. Dê o primeiro soco para iniciar a luta.';
  }catch(e){}
}
function update(){
  $('power').textContent=power; $('workouts').textContent=workouts; $('level').textContent=level;
  $('playerbar').style.width=(Math.max(0,playerHP)/playerMaxHP*100)+'%';
  $('enemybar').style.width=(Math.max(0,enemyHP)/enemyMaxHP*100)+'%';
  $('playerhp').textContent=Math.max(0,playerHP)+' / '+playerMaxHP;
  $('enemyhp').textContent=Math.max(0,enemyHP)+' / '+enemyMaxHP;
  $('enemyname').textContent='OPONENTE #'+enemyNumber;
  $('phaseBox').textContent='🏆 FASE '+enemyNumber;
  $('ultimateTrainingCard').classList.toggle('hidden', !(phase30Cleared || enemyNumber>30));
  $('tutorialCompleteCard').classList.toggle('hidden', !(tutorialCompleteUnlocked || enemyNumber>=100));
  $('progressBar').style.width=(workouts%10/10*100)+'%';
  $('progressText').textContent=(workouts%10)+' / 10';
  $('gymmsg').innerHTML='Força: <b>'+power+'</b> · Vida máxima: <b>'+playerMaxHP+'</b> · Resistência: <b>'+resistance+'</b>. Bora ficar mais forte!';
  saveProgress();
}
function show(which){view=which;$('fight').classList.toggle('active',which==='fight');$('gym').classList.toggle('active',which==='gym');$('mode').textContent=which==='gym'?'MODO TREINO':'MODO LUTA';saveProgress();}
$('openGym').addEventListener('click',()=>show('gym'));
$('backFight').addEventListener('click',()=>show('fight'));
$('regenerate').addEventListener('click',()=>{
  playerMaxHP+=10;
  playerHP=Math.min(playerMaxHP,playerHP+25);
  workouts++;
  $('gymmsg').textContent='❤️ Regeneração concluída! +25 de vida e +10 de vida máxima.';
  $('msg').textContent='❤️ Treino de regeneração: sua vida máxima agora é '+playerMaxHP+'.';
  update();
});
$('resistance').addEventListener('click',()=>{
  resistance++;
  workouts++;
  $('gymmsg').textContent='🛡️ Resistência aumentada! O dano atual dos oponentes é '+Math.max(1,(3+(enemyNumber-1)*2)-resistance*2)+'. Oponentes mais fortes podem superar sua resistência; treine mais para aguentar.';
  $('msg').textContent='🛡️ Resistência nível '+resistance+': dano recebido reduzido.';
  update();
});
document.querySelectorAll('.train').forEach(button=>button.addEventListener('click',()=>{
  const gain=Number(button.dataset.gain), name=button.dataset.name;
  power+=gain; workouts++;
  let message='💪 Você treinou '+name+'! +'+gain+' de força.';
  if(workouts%10===0){level++;power+=2;message+=' SUBIU DE NÍVEL! +2 de força bônus!';}
  $('gymmsg').textContent=message; update(); $('gymmsg').innerHTML=message;
}));
function spawnNextEnemy(){
  if(playerHP<=0)return;
  fightStarted=false;
  enemyNumber++;enemyMaxHP=100+(enemyNumber-1)*75+Math.pow(enemyNumber-1,2)*8;enemyHP=enemyMaxHP;
  $('enemy').textContent=['🥊','🥷','🤼','👊','🥋'][(enemyNumber-1)%5];
  $('msg').textContent='⚠️ Oponente #'+enemyNumber+' chegou! Ele tem '+enemyMaxHP+' de vida.';update();
}
function enemyAttack(){
  if(view!=='fight'||!fightStarted||enemyHP<=0||playerHP<=0)return;
  const enemyPower=8+(enemyNumber-1)*5+Math.floor(Math.pow(enemyNumber-1,1.35));const damage=guarding?0:Math.max(1,enemyPower-resistance*3);playerHP=Math.max(0,playerHP-damage);
  if(playerHP<=0){guarding=false;endGuard();$('msg').textContent='💥 Você foi derrotado! Toque em NOVA LUTA para tentar novamente.';}
  else if(guarding){$('msg').textContent='🛡️ Defesa perfeita! Você ficou imune e não recebeu dano!';}
  update();
}
$('punch').addEventListener('click',()=>{
  if(view!=='fight')return;
  if(playerHP<=0){$('msg').textContent='Você foi derrotado! Toque em NOVA LUTA para recomeçar.';return;}
  if(enemyHP<=0)return;
  fightStarted=true;
  const damage=power;enemyHP=Math.max(0,enemyHP-damage);
  $('hero').style.transform='translateX(12px) rotate(-10deg)';$('enemy').style.transform='translateX(12px) rotate(12deg)';
  setTimeout(()=>{$('hero').style.transform='';$('enemy').style.transform='';},140);
  if(enemyHP<=0){playerHP=playerMaxHP;if(enemyNumber>=30){phase30Cleared=true;showConfetti();}$('msg').textContent='🏆 FASE '+enemyNumber+' concluída! Você derrotou o oponente! ❤️ Sua vida foi restaurada! Próxima fase chegando...';if(nextEnemyTimeout)clearTimeout(nextEnemyTimeout);nextEnemyTimeout=setTimeout(()=>{if(playerHP>0&&enemyHP<=0)spawnNextEnemy();},650);}
  else $('msg').textContent='👊 Você acertou '+damage+' de dano!';
  update();
});
const guardBtn=$('guard');
function startGuard(e){if(e)e.preventDefault();if(playerHP<=0)return;guarding=true;guardBtn.textContent='🛡️ DEFENDENDO';guardBtn.classList.add('green');$('msg').textContent='🛡️ Você está defendendo! Segure o botão.';if(e&&guardBtn.setPointerCapture&&e.pointerId!==undefined){try{guardBtn.setPointerCapture(e.pointerId)}catch(_){}}}
function endGuard(){guarding=false;guardBtn.textContent='🛡️ DEFENDER';guardBtn.classList.remove('green');}
guardBtn.addEventListener('pointerdown',startGuard);
guardBtn.addEventListener('pointerup',endGuard);
guardBtn.addEventListener('pointercancel',endGuard);
guardBtn.addEventListener('lostpointercapture',endGuard);
guardBtn.addEventListener('contextmenu',e=>e.preventDefault());
$('ultimateTraining').addEventListener('click',()=>{
  if(!(phase30Cleared || enemyNumber>30))return;
  power+=100;playerMaxHP+=100;playerHP=Math.min(playerMaxHP,playerHP+100);workouts++;
  $('gymmsg').textContent='🌟 TREINO COMPLETO! +100 de força, +100 de vida máxima e +100 de vida recuperada. Você pode usar este treino quantas vezes quiser!';
  $('msg').textContent='🌟 Treino Completo usado! +100 de força e +100 de vida máxima/recuperada. Pode repetir quando quiser!';update();
});
$('tutorialComplete').addEventListener('click',()=>{
  if(!(tutorialCompleteUnlocked || enemyNumber>=100))return;
  tutorialCompleteUnlocked=true;
  const code=prompt('TUTORIAL COMPLETO 👑\nDigite seu código para receber o bônus:\n12345678910 = ADM (+1.000.000 de cada atributo)\nplay 2 = Jogador (+1.000 de cada atributo)');
  if(code===null)return;
  const normalizedCode=code.trim().toLowerCase();
  const isAdmin=normalizedCode==='12345678910';
  const isPlayer=normalizedCode==='play 2';
  if(!isAdmin&&!isPlayer){
    $('gymmsg').textContent='❌ Código inválido. Digite 12345678910 (ADM) ou play 2 (jogador).';
    $('msg').textContent='❌ Código inválido. Nenhum atributo foi alterado.';
    return;
  }
  const bonus=isAdmin?1000000:1000;
  power+=bonus;playerMaxHP+=bonus;playerHP=Math.min(playerMaxHP,playerHP+bonus);resistance+=bonus;workouts++;
  const label=bonus.toLocaleString('pt-BR');
  $('gymmsg').textContent=(isAdmin?'👑 ADM CONFIRMADO! ':'🎉 TUTORIAL COMPLETO! ')+'+'+label+' de força, +'+label+' de vida máxima/recuperada e +'+label+' de resistência.';
  $('msg').textContent=(isAdmin?'👑 Bônus ADM aplicado! ':'🎉 Bônus de jogador aplicado! ')+'+'+label+' em força, vida e resistência.';update();
});
function showConfetti(){
  let layer=document.querySelector('.confetti-layer');if(!layer){layer=document.createElement('div');layer.className='confetti-layer';document.body.appendChild(layer);}
  layer.innerHTML='';const colors=['#ff5964','#ffd166','#70e6a1','#80bfff','#d6a4ff','#ffffff'];
  for(let i=0;i<90;i++){const piece=document.createElement('i');piece.className='confetti-piece';piece.style.left=Math.random()*100+'%';piece.style.background=colors[i%colors.length];piece.style.animationDuration=(2.4+Math.random()*2.8)+'s';piece.style.animationDelay=(Math.random()*1.2)+'s';piece.style.transform='rotate('+Math.random()*360+'deg)';layer.appendChild(piece);}
  setTimeout(()=>{if(layer&&layer.parentNode)layer.remove();},6500);
}
$('reset').addEventListener('click',()=>{
  if(nextEnemyTimeout)clearTimeout(nextEnemyTimeout);nextEnemyTimeout=null;
  playerMaxHP=100;playerHP=100;resistance=0;enemyNumber=1;enemyMaxHP=100;enemyHP=100;fightStarted=false;phase30Cleared=false;tutorialCompleteUnlocked=false;endGuard();$('enemy').textContent='🥊';
  $('msg').textContent='Nova luta! FASE 1. Toque em DAR SOCO para atacar.';show('fight');update();
});
// O oponente só começa a tentar atacar a cada 275 ms depois do primeiro soco do jogador em cada fase.
setInterval(enemyAttack,275);
let sx=0,sy=0;
document.addEventListener('touchstart',e=>{if(e.changedTouches.length){sx=e.changedTouches[0].clientX;sy=e.changedTouches[0].clientY;}},{passive:true});
document.addEventListener('touchend',e=>{if(!e.changedTouches.length)return;const dx=e.changedTouches[0].clientX-sx,dy=e.changedTouches[0].clientY-sy;if(Math.abs(dx)>80&&Math.abs(dx)>Math.abs(dy)*1.3){if(dx<0)show('gym');else show('fight');}},{passive:true});
loadProgress();update();
</script></body></html>