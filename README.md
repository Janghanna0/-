<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>데이원컴퍼니 강의 카탈로그</title>
<link href="https://fonts.googleapis.com/css2?family=Pretendard:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #13131a;
    --surface2: #1c1c28;
    --border: #2a2a3d;
    --accent: #7c6ef5;
    --accent2: #f5c842;
    --text: #e8e8f0;
    --text-muted: #6b6b85;
    --new: #3ecf8e;
    --ai: #a78bfa;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Pretendard', 'Apple SD Gothic Neo', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ─── HEADER ─── */
  .header {
    padding: 60px 48px 40px;
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    border-bottom: 1px solid var(--border);
  }
  .header-logo {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: rgb(243, 174, 174);
    margin-bottom: 10px;
  }
  .header h1 {
    font-size: clamp(28px, 3.5vw, 44px);
    font-weight: 800;
    letter-spacing: -0.03em;
    line-height: 1.1;
  }
  .header h1 span { color: var(--accent); }
  .header-meta {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 6px;
  }
  .header-stats {
    display: flex;
    align-items: center;
    gap: 20px;
  }
  .header-stats .stat {
    text-align: right;
    line-height: 1.2;
  }
  .header-stats .stat strong {
    font-size: 32px;
    font-weight: 800;
    color: var(--accent2);
    letter-spacing: -0.03em;
    display: block;
  }
  .header-stats .stat span {
    font-size: 11.5px;
    color: var(--text-muted);
  }
  .header-stats .stat-divider {
    width: 1px;
    height: 30px;
    background: var(--border);
  }
  .header-caption {
    font-size: 12px;
    color: var(--text-muted);
  }

  /* ─── SEARCH ─── */
  .search-wrapper {
    padding: 24px 48px 0;
  }
  .search-box {
    display: flex;
    align-items: center;
    gap: 10px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 16px;
    max-width: 480px;
    color: var(--text-muted);
    transition: border-color 0.2s;
  }
  .search-box:focus-within { border-color: var(--accent); }
  .search-box input {
    flex: 1;
    background: transparent;
    border: none;
    outline: none;
    color: var(--text);
    font-size: 14px;
    font-family: inherit;
  }
  .search-box input::placeholder { color: var(--text-muted); }
  .search-clear {
    background: none;
    border: none;
    color: var(--text-muted);
    cursor: pointer;
    font-size: 13px;
    padding: 2px 4px;
  }
  .search-clear:hover { color: var(--text); }
  .search-results-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 14px;
  }
  .search-empty {
    color: var(--text-muted);
    font-size: 14px;
    padding: 40px 0;
    text-align: center;
  }

  /* ─── CATEGORY TABS ─── */
  .tabs-wrapper {
    padding: 28px 48px 0;
    position: sticky;
    top: 0;
    background: var(--bg);
    z-index: 100;
    border-bottom: 1px solid var(--border);
  }
  .tabs {
    display: flex;
    gap: 4px;
    overflow-x: auto;
    scrollbar-width: none;
    padding-bottom: 0;
  }
  .tabs::-webkit-scrollbar { display: none; }
  .tab {
    flex-shrink: 0;
    padding: 10px 20px;
    border-radius: 8px 8px 0 0;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    border: none;
    background: transparent;
    color: var(--text-muted);
    transition: all 0.2s;
    position: relative;
    bottom: -1px;
    border: 1px solid transparent;
    border-bottom: none;
  }
  .tab:hover { color: var(--text); background: var(--surface); }
  .tab.active {
    color: var(--text);
    background: var(--surface);
    border-color: var(--border);
    border-bottom-color: var(--surface);
  }

  /* ─── SECTION ─── */
  .section {
    display: none;
    padding: 40px 48px 60px;
  }
  .section.active { display: block; }

  .section-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 28px;
  }
  .section-title {
    font-size: 20px;
    font-weight: 700;
  }
  .section-count {
    font-size: 13px;
    color: var(--text-muted);
  }
  .nav-btns {
    display: flex;
    gap: 8px;
  }
  .nav-btn {
    width: 36px; height: 36px;
    border-radius: 50%;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--text);
    cursor: pointer;
    font-size: 16px;
    display: flex; align-items: center; justify-content: center;
    transition: all 0.2s;
  }
  .nav-btn:hover { background: var(--accent); border-color: var(--accent); }
  .nav-btn:disabled { opacity: 0.3; cursor: not-allowed; }
  .nav-btn:disabled:hover { background: var(--surface); border-color: var(--border); }

  /* ─── CAROUSEL ─── */
  .carousel-outer {
    overflow: hidden;
    border-radius: 12px;
  }
  .carousel-track {
    display: flex;
    align-items: stretch;
    gap: 14px;
    transition: transform 0.45s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    will-change: transform;
  }

  /* ─── CARD ─── */
  .card {
    flex: 0 0 calc((100% - 4*14px) / 5);
    display: flex;
    flex-direction: column;
    background: var(--surface);
    border-radius: 10px;
    border: 1px solid var(--border);
    overflow: hidden;
    transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
    cursor: pointer;
  }
  .card:hover {
    transform: translateY(-3px);
    border-color: var(--accent);
    box-shadow: 0 8px 28px rgba(124, 110, 245, 0.15);
  }
  a.card {
    text-decoration: none;
    color: inherit;
  }
  .card-nolink { cursor: default; }
  .card-nolink:hover {
    transform: none;
    border-color: var(--border);
    box-shadow: none;
  }
  .card-thumb {
    width: 100%;
    aspect-ratio: 16/9;
    object-fit: cover;
    display: block;
    background: var(--surface2);
    position: relative;
    overflow: hidden;
    flex-shrink: 0;
  }
  .card-thumb-svg {
    width: 100%;
    aspect-ratio: 16/9;
    display: block;
  }
  .card-body {
    padding: 12px 14px 14px;
    display: flex;
    flex-direction: column;
    flex: 1;
  }
  .card-badges {
    display: flex;
    gap: 4px;
    margin-bottom: 8px;
    flex-wrap: wrap;
  }
  .badge {
    font-size: 8.5px;
    font-weight: 700;
    letter-spacing: 0.06em;
    padding: 2px 6px;
    border-radius: 4px;
    text-transform: uppercase;
  }
  .badge-sub {
    background: var(--surface2);
    color: var(--text-muted);
    border: 1px solid var(--border);
  }
  .badge-ai {
    background: rgba(167, 139, 250, 0.15);
    color: var(--ai);
    border: 1px solid rgba(167, 139, 250, 0.3);
  }
  .badge-new {
    background: rgba(62, 207, 142, 0.15);
    color: var(--new);
    border: 1px solid rgba(62, 207, 142, 0.3);
  }
  .card-title {
    font-size: 12px;
    font-weight: 600;
    line-height: 1.4;
    margin-bottom: 10px;
  }
  .card-meta {
    display: flex;
    flex-wrap: wrap;
    gap: 8px 10px;
    font-size: 9.5px;
    color: var(--text-muted);
    border-top: 1px solid var(--border);
    padding-top: 9px;
    margin-top: auto;
  }
  .card-meta-item {
    display: flex;
    align-items: center;
    gap: 3px;
  }
  .card-meta-item svg { opacity: 0.6; width: 10px; height: 10px; }

  @media (max-width: 1100px) {
    .card { flex: 0 0 calc((100% - 3*14px) / 4); }
  }
  @media (max-width: 900px) {
    .header { padding: 40px 24px 28px; flex-direction: column; align-items: flex-start; gap: 16px; }
    .header-meta { text-align: left; }
    .tabs-wrapper { padding: 20px 24px 0; }
    .search-wrapper { padding: 20px 24px 0; }
    .section { padding: 28px 24px 48px; }
    .card { flex: 0 0 calc((100% - 14px) / 2); }
  }
  @media (max-width: 600px) {
    .card { flex: 0 0 70%; }
  }
</style>
</head>
<body>

<header class="header">
  <div>
    <div class="header-logo">Day1 Company</div>
    <h1>디지털 아카이브<br><span>강의 카탈로그</span></h1>
    <p>상자를 클릭하면 강의 소개 페이지로 연결됩니다.</p>
  </div>
  <div class="header-meta">
    <div class="header-stats">
      <div class="stat">
        <strong>279</strong>
        <span>개 콘텐츠</span>
      </div>
      <div class="stat-divider"></div>
      <div class="stat">
        <strong>3,000+</strong>
        <span>개 강의</span>
      </div>
    </div>
    <div class="header-caption">2026 최신판</div>
  </div>
</header>

<div class="search-wrapper">
  <div class="search-box">
    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
    <input type="text" id="searchInput" placeholder="강의명, 툴, 카테고리로 검색...">
    <button id="searchClear" class="search-clear" style="display:none;">✕</button>
  </div>
</div>

<div class="tabs-wrapper" id="tabsWrapper">
  <div class="tabs" id="tabs"></div>
</div>

<div id="searchResults" class="search-section" style="display:none; padding: 24px 48px 60px;"></div>
<div id="sections"></div>

<script>
const CATEGORIES = [
  {
    id: 'ai', label: '🤖 AI', count: 15,
    courses: [
      { no:1, title:'바쁜 현대인을 위한 AI 추월차선, 전문가 4인이 엄선한 필수 활용법', sub:'AI 활용/생산성', year:'2025.08', tools:'ChatGPT, 미드저니, Claude', hours:'26시간 44분', sessions:113, ai:true, new:true, link:'https://fastcampus.co.kr/data_online_aipassing', theme:['#6c5ce7','#a29bfe'] },
      { no:2, title:'클로드 코드로 24시간 Full 가동! 100명 규모 AI 조직 운영 자동화 구축하기', sub:'AI 자동화', year:'2026.05', tools:'', hours:'19시간 17분', sessions:59, ai:true, new:true, link:'https://fastcampus.co.kr/dgn_online_24fullclaude?utm_source=google&utm_medium=cpc&utm_campaign=fassker^260506^000000&utm_content=%ED%81%B4%EB%A1%9C%EB%93%9C%20ai&utm_term=&gad_source=1&gad_campaignid=23823983250&gbraid=0AAAAADdsH6dcts1rDwwHN-LzNKOtTNs4q&gclid=CjwKCAjw0o3SBhBVEiwAh28-jaEFfokLjmeiX_PqoSkXAcQGiAvPYz4xBMtr5ybpRoR2ttlNcmsqXRoCwy8QAvD_BwE', theme:['#00cec9','#81ecec'] },
      { no:3, title:'일잘러를 위한 클로드 코드 입문 바이블 : 현실적인 30가지 업무 자동화&생산성 프로젝트', sub:'AI 자동화', year:'2026.05', tools:'', hours:'20시간 09분', sessions:69, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_claudecodebible', theme:['#fd79a8','#e84393'] },
      { no:4, title:'AI 시대, 누구나 1시간만에 제작하는 UI 프로토타이핑 가이드 (w. figma MAKE, Cursor)', sub:'AI 코딩', year:'2025.10', tools:'figma MAKE, Cursor', hours:'10시간 23분', sessions:48, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_figmamake', theme:['#e17055','#fab1a0'] },
      { no:5, title:'2025 AI 시대 일잘러를 위한 비현실적인 700가지 ChatGPT 활용 바이블', sub:'AI 활용/생산성', year:'2025.07', tools:'ChatGPT', hours:'122시간 33분', sessions:512, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_chatgpt700', theme:['#0984e3','#74b9ff'] },
      { no:6, title:'AI 활용 비즈니스 적용 플레이북 : 실무에서 바로 쓰는 이미지·텍스트 위주 실무형 결과물 제작', sub:'AI 활용/생산성', year:'2025.04', tools:'ChatGPT', hours:'23시간 32분', sessions:80, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_pbaibusiness', theme:['#00b894','#55efc4'] },
      { no:7, title:'지금 당장 나만의 서비스 런칭! 13가지 초!고퀄리티 웹 서비스로 Cursor AI 마스터', sub:'AI 코딩', year:'2025.03', tools:'Cursor AI', hours:'23시간 01분', sessions:137, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_webcursorai', theme:['#fdcb6e','#e17055'] },
      { no:8, title:'[직:장인(匠人)] ChatGPT 없이 일 못 하는 시대 : 검색창이 아닌 업무 도구로의 ChatGPT 실무 사용법', sub:'AI 활용/생산성', year:'2025.11', tools:'ChatGPT', hours:'5시간 03분', sessions:50, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_chatgptpromptdesign', theme:['#6c5ce7','#a29bfe'] },
      { no:9, title:'[직:장인(匠人)] 프롬프트, 검색이 아니라 명령이다. : 입문자를 위한 10가지 ChatGPT 실무 활용법', sub:'AI 활용/생산성', year:'2025.11', tools:'ChatGPT', hours:'4시간 54분', sessions:50, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_promptascommand', theme:['#00cec9','#81ecec'] },
      { no:10, title:'2025 일잘러를 위한 업무 속도 10배 높이는 구글 AI : Gemini 바이블', sub:'AI 활용/생산성', year:'2025.08', tools:'Gemini', hours:'11시간 41분', sessions:57, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_gemini', theme:['#fd79a8','#e84393'] },
      { no:11, title:'MCP x n8n으로 이제야 실현하는 AI 자동화', sub:'AI 자동화', year:'2025.07', tools:'MCP, n8n', hours:'13시간 33분', sessions:36, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_mcpn8n', theme:['#e17055','#fab1a0'] },
      { no:12, title:'n8n 하나로 끝내는 AI 자동화의 모든 것', sub:'AI 자동화', year:'2025.06', tools:'n8n', hours:'30시간 53분', sessions:102, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_n8n', theme:['#0984e3','#74b9ff'] },
      { no:13, title:'자동화 외길인생 윤자동의 Cursor AI 업무자동화', sub:'AI 자동화', year:'2025.02', tools:'Cursor AI', hours:'10시간 30분', sessions:6, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_yunjadong', theme:['#00b894','#55efc4'] },
      { no:14, title:'Nano Banana & Gemini로 완성하는 FULL AI-BX 프로세스', sub:'AI 활용/생산성', year:'2026.05', tools:'', hours:'8시간 31분', ai:true, new:true, link:'https://fastcampus.co.kr/dgn_online_NanoBananaBX', theme:['#fdcb6e','#e17055'] },
      { no:15, title:'바이브코딩 앱 개발 바이블 : 퇴근 후 나 홀로 1인 앱 & 게임 개발로 수익화 시작!', sub:'AI 코딩', year:'2026.05', tools:'', hours:'21시간 45분', ai:true, new:true, link:'https://fastcampus.co.kr/data_online_appvibecoding', theme:['#6c5ce7','#a29bfe'] },
    ]
  },
  {
    id: 'design', label: '🎨 디자인', count: 35,
    courses: [
      { no:16, title:'장면 설계부터 감정연기까지, AI 영화 제작 클래스', sub:'영상/사진', year:'2025.05', tools:'미드저니, ComfyUI, Claude', hours:'8시간 18분', sessions:68, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_aimovie', theme:['#6c5ce7','#a29bfe'] },
      { no:17, title:'입문자를 위한 AI 100일 챌린지 : SNS 콘텐츠부터 감도높은 영상 제작 KIT', sub:'영상/사진', year:'2025.06', tools:'미드저니, ChatGPT, Runway', hours:'36시간 08분', sessions:154, ai:true, new:true, link:'https://fastcampus.co.kr/dgn_online_AI100day', theme:['#00cec9','#81ecec'] },
      { no:18, title:'쇼미더머니2, MAMA를 브랜딩한 크리에이티브 디렉터에게 배우는, AI 커머셜 아트웍&영상 제작', sub:'영상/사진', year:'2025.06', tools:'미드저니, 어도비', hours:'17시간 20분', sessions:43, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_aicommercial', theme:['#fd79a8','#e84393'] },
      { no:19, title:'외주 없이, AI로 완성하는 맛깔나는 배달·외식·카페 콘텐츠 1인 제작법 w. 스튜디오 끼니', sub:'영상/사진', year:'2025.06', tools:'미드저니, 어도비, ChatGPT', hours:'10시간 18분', sessions:32, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_ggini', theme:['#e17055','#fab1a0'] },
      { no:20, title:'상상력을 자극하는 AI 애니메이션 영상 제작', sub:'영상/사진', year:'2025.05', tools:'미드저니, ChatGPT, ComfyUI', hours:'21시간 23분', sessions:76, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_aianimation', theme:['#0984e3','#74b9ff'] },
      { no:21, title:'디자이너를 위한 AI 활용 브랜드 룩북 제작', sub:'브랜드/커머셜', year:'2025.05', tools:'미드저니, Kling, 포토샵', hours:'20시간 56분', sessions:51, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_ai_fashion', theme:['#00b894','#55efc4'] },
      { no:22, title:'포즈 장인에게 배우는 AI 캐릭터 : 100가지 역동적인 포즈 제작 w. WebUI', sub:'캐릭터/게임아트', year:'2025.05', tools:'Stable Diffusion WebUI', hours:'7시간 30분', sessions:5, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_webui100', theme:['#fdcb6e','#e17055'] },
      { no:23, title:'AI로 완성하는 5가지 감도높은 광고 제작 : 이미지, 음악, 영상, 편집까지', sub:'영상/사진', year:'2025.04', tools:'미드저니, 어도비, ComfyUI', hours:'11시간 45분', ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_aiads', theme:['#6c5ce7','#a29bfe'] },
      { no:24, title:'AI로 감각을 더한 키치한 굿즈 제작', sub:'브랜드/커머셜', year:'2025.04', tools:'미드저니, 어도비, ChatGPT', hours:'8시간 01분', sessions:7, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_aigoods', theme:['#00cec9','#81ecec'] },
      { no:25, title:'100가지 ComfyUI 워크플로우로 완성하는 1,000개 AI 이미지/영상', sub:'영상/사진', year:'2025.03', tools:'미드저니, ComfyUI', hours:'21시간 29분', sessions:84, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_comfyui1000', theme:['#fd79a8','#e84393'] },
      { no:26, title:'게임 원화가가 되기 위한 : 차별화된 AI 어시스트로 완성하는 고퀄리티 게임 원화', sub:'캐릭터/게임아트', year:'2025.03', tools:'블랜더, 포토샵, ComfyUI', hours:'9시간 14분', sessions:5, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_fruitbk', theme:['#e17055','#fab1a0'] },
      { no:27, title:'미드저니 스타일 레퍼런스 코드로 만드는 감도높은 AI 아트웍 1000종+', sub:'영상/사진', year:'2025.02', tools:'미드저니', hours:'7시간 45분', sessions:28, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_sref', theme:['#0984e3','#74b9ff'] },
      { no:28, title:'8시간만에 마스터하는 미드저니 초단기 완성반', sub:'영상/사진', year:'2025.01', tools:'미드저니', hours:'7시간 33분', sessions:21, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_mj8h', theme:['#00b894','#55efc4'] },
      { no:29, title:'라이엇 Principal TA 오문영의 AI 인게임 & 시네마틱 풀 프로덕션 마스터 클래스', sub:'캐릭터/게임아트', year:'2025.09', tools:'미드저니, ChatGPT', hours:'55시간 02분', ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_riot', theme:['#fdcb6e','#e17055'] },
      { no:30, title:'갓 오브 워\' 배경 제작자 최섭의 AAA 게임 배경 제작', sub:'캐릭터/게임아트', year:'2025.04', tools:'미드저니, 어도비, Zbrush', hours:'34시간 41분', ai:true, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:31, title:'[쉐어엑스] Stable Diffusion, ComfyUI로 배우는 AI 영상 프로젝트 by 컴파운드컬렉티브', sub:'영상/사진', year:'2025.07', tools:'Stable Diffusion, ComfyUI', hours:'6시간 36분', sessions:35, ai:true, new:false, link:'https://sharex.fastcampus.co.kr/dgn_online_ccai', theme:['#00cec9','#81ecec'] },
      { no:32, title:'미드저니 하나로 끝내는 : 뉴비 맞춤형 비주얼 콘텐츠 120% 활용 제작 가이드', sub:'영상/사진', year:'2025.05', tools:'미드저니', hours:'10시간 09분', sessions:51, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_areshocked', theme:['#fd79a8','#e84393'] },
      { no:33, title:'AI 코스메틱 마스터 패키지 : 일관성을 유지하는 커머셜 아트웍의 모든 것', sub:'브랜드/커머셜', year:'2025.06', tools:'ChatGPT, 미드저니', hours:'13시간 21분', sessions:51, ai:true, new:true, link:'https://fastcampus.co.kr/dgn_online_aicosmetic', theme:['#e17055','#fab1a0'] },
      { no:34, title:'ElevenLabs 글로벌 해커톤 수상작 리뷰부터 음성 AI 어플리케이션 개발까지', sub:'영상/사진', year:'2025.05', tools:'ChatGPT, 코드 에디터(cursor, vscord 등)', hours:'11시간 27분', sessions:45, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_elevenlabs', theme:['#0984e3','#74b9ff'] },
      { no:35, title:'혼자서도 프로처럼! 포론포의 버추얼 MV 제작 마스터 클래스', sub:'영상/사진', year:'2025.06', tools:'Unity, 프리미어 프로', hours:'8시간 40분', sessions:6, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_plpo', theme:['#00b894','#55efc4'] },
      { no:36, title:'나의 첫 Live2D 리깅 입문, 제로부터 시작하는 리깅 마스터 패키지', sub:'캐릭터/게임아트', year:'2025.05', tools:'Live2D cubism, 클립스튜디오', hours:'29시간 38분', sessions:23, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_yurancoco', theme:['#fdcb6e','#e17055'] },
      { no:37, title:'한 번에 끝내는 블렌더 초격차 패키지 2025', sub:'3D/블렌더', year:'2025.04', tools:'블렌더', hours:'132시간 30분', sessions:69, ai:false, new:true, link:'https://fastcampus.co.kr/dgn_online_blenderkit', theme:['#6c5ce7','#a29bfe'] },
      { no:38, title:'Blender로 완성하는 인스타그래머블 3D 키비주얼 아트웍', sub:'3D/블렌더', year:'2025.04', tools:'블렌더', hours:'44시간 48분', sessions:28, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_InstaBlender', theme:['#00cec9','#81ecec'] },
      { no:39, title:'버츄얼 방송 퀄리티 업! 블렌더로 완성하는 맞춤형 배경 제작', sub:'3D/블렌더', year:'2025.04', tools:'블렌더', hours:'13시간 43분', sessions:11, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_blender_vtuber', theme:['#fd79a8','#e84393'] },
      { no:40, title:'쉿! 디자이너도 몰래듣는\' 에이핫의 포스터 디자인 트레이닝', sub:'포스터/일러스트', year:'2025.03', tools:'일러스트레이터, 포토샵', hours:'9시간 36분', sessions:8, ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:41, title:'매력적인 선으로 이어지는 완성형 캐주얼 일러스트 : 드로잉 테크닉의 모든 것 by. 요츠미 시로', sub:'포스터/일러스트', year:'2025.02', tools:'클립스튜디오', hours:'14시간 52분', sessions:6, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_linedrawing', theme:['#0984e3','#74b9ff'] },
      { no:42, title:'흐스흐 작가의 몽글몽글 아이패드 드로잉 : 기초부터 수익화까지', sub:'포스터/일러스트', year:'2025.02', tools:'Procreate', hours:'7시간 57분', sessions:6, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_huseuhu', theme:['#00b894','#55efc4'] },
      { no:43, title:'Mmmmonexx의 역동적인 캐릭터로 배우는 탄탄한 일러스트 입문', sub:'포스터/일러스트', year:'2025.01', tools:'Procreate', hours:'17시간 31분', sessions:12, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_mmmmonexx', theme:['#fdcb6e','#e17055'] },
      { no:44, title:'[쉐어엑스] BKID 프로젝트 실습으로 배우는 제품 디자인 실무', sub:'영상/사진', year:'2025.07', tools:'미드저니, ChatGPT, Keyshot', hours:'21시간 20분', sessions:9, ai:false, new:false, link:'https://sharex.fastcampus.co.kr/dgn_online_bkid', theme:['#6c5ce7','#a29bfe'] },
      { no:45, title:'나의 첫 영상 수업, 거트루드의 캡컷 완성반', sub:'포스터/일러스트', year:'2025.02', tools:'캡컷', hours:'19시간 47분', sessions:11, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_capcut', theme:['#00cec9','#81ecec'] },
      { no:46, title:'3D 아티스트 여울이 알려주는 : 블렌더를 활용한 원화 퀄리티의 3D 모델링부터 버튜버 데뷔까지', sub:'3D/블렌더', year:'2025.01', tools:'블렌더', hours:'62시간 31분', sessions:24, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_online_yeoul', theme:['#fd79a8','#e84393'] },
      { no:47, title:'The RED : 디즈니 애니메이터 윤나라의 세계에서 사랑받는 캐릭터의 비밀', sub:'캐릭터/게임아트', year:'2025.01', tools:'', hours:'9시간 06분', sessions:6, ai:false, new:false, link:'https://fastcampus.co.kr/dgn_red_disney', theme:['#e17055','#fab1a0'] },
      { no:48, title:'2026 한 번에 끝내는 피그마 초격차 패키지', sub:'웹/UX 디자인', year:'2025.09', tools:'피그마', hours:'15시간 29분', sessions:9, ai:true, new:true, link:'https://fastcampus.co.kr/dgn_online_figmasig', theme:['#0984e3','#74b9ff'] },
      { no:49, title:'하루 2시간, 월 1천만 원을 벌 수 있는 외주 디자이너의 성공 방정식 with Framer', sub:'웹/UX 디자인', year:'2025.03', tools:'Framer', hours:'32시간 39분', sessions:15, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_framer', theme:['#00b894','#55efc4'] },
      { no:50, title:'성공하는 UX/UI 디자이너의 필수 스킬셋: 실무에서 인정받는 5가지 핵심역량', sub:'웹/UX 디자인', year:'2025.01', tools:'', hours:'30시간 42분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
    ]
  },
  {
    id: 'data', label: '📊 데이터', count: 28,
    courses: [
      { no:51, title:'코드 한 줄 없이 실전 RAG 구축 가이드 : No-Code RAG 6가지 프로젝트', sub:'AI 모델 개발', year:'2025.04', tools:'n8n, Microsoft Azure, claude', hours:'13시간 04분', sessions:7, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_nocoderag', theme:['#6c5ce7','#a29bfe'] },
      { no:52, title:'ROS 2로 시작하는 로보틱스 Motion Planning', sub:'머신러닝/로보틱스', year:'2025.05', tools:'ROS 2', hours:'25시간 31분', sessions:249, ai:false, new:false, link:'https://fastcampus.co.kr/data_online_mp', theme:['#00cec9','#81ecec'] },
      { no:53, title:'Mobile ALOHA와 모방 학습을 활용한 로봇 행동 제어', sub:'머신러닝/로보틱스', year:'2025.05', tools:'Mobile ALOHA', hours:'18시간 56분', sessions:41, ai:false, new:false, link:'https://fastcampus.co.kr/data_online_il', theme:['#fd79a8','#e84393'] },
      { no:54, title:'협동로봇 개발을 위한 다관절 로봇 티칭과 구현', sub:'머신러닝/로보틱스', year:'2025.02', tools:'', hours:'14시간 15분', sessions:9, ai:false, new:false, link:'https://fastcampus.co.kr/data_online_articulatedrobot', theme:['#e17055','#fab1a0'] },
      { no:55, title:'Azure OpenAI – 엔터프라이즈급 RAG 시스템 설계와 보안 인프라', sub:'AI 모델 개발', year:'2025.05', tools:'Microsoft Azure', hours:'3시간 49분', sessions:28, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_azure', theme:['#0984e3','#74b9ff'] },
      { no:56, title:'MCP로 엔터프라이즈 환경에서 AI Agent 활용 및 제어', sub:'AI 모델 개발', year:'2025.04', tools:'Cursor ai', hours:'12시간 25분', sessions:38, ai:true, new:true, link:'https://fastcampus.co.kr/data_online_mcp', theme:['#00b894','#55efc4'] },
      { no:57, title:'모두의 AI 케인의 Agent로 완성하는 RAG : 데이터 별 아키텍처 설계를 중심으로', sub:'AI 모델 개발', year:'2025.03', tools:'LLM, RAG', hours:'30시간 53분', sessions:119, ai:true, new:false, link:'https://fastcampus.co.kr/dev_online_aiagent2', theme:['#fdcb6e','#e17055'] },
      { no:58, title:'MS Copilot AI 개발자의 RAG 마스터 클래스 : 상황에 맞는 RAG 선택과 성능 최적화', sub:'AI 모델 개발', year:'2025.03', tools:'RAG', hours:'24시간 24분', sessions:110, ai:true, new:false, link:'https://fastcampus.co.kr/data_red_ragmaster', theme:['#6c5ce7','#a29bfe'] },
      { no:59, title:'오픈소스 LLM으로 인프라 투자 없이 고성능 AI 모델 개발하기', sub:'AI 모델 개발', year:'2025.03', tools:'LLM', hours:'15시간 58분', sessions:15, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_llmai', theme:['#00cec9','#81ecec'] },
      { no:60, title:'파인튜닝과 RAG로 완성하는 도메인 맞춤형 LLM 서비스 개발', sub:'AI 모델 개발', year:'2025.02', tools:'LLM, RAG', hours:'44시간 08분', sessions:24, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_fine', theme:['#fd79a8','#e84393'] },
      { no:61, title:'랭그래프로 한번에 완성하는 복잡한 RAG와 Agent', sub:'AI 모델 개발', year:'2025.02', tools:'RAG', hours:'17시간 45분', sessions:39, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_langgraph', theme:['#e17055','#fab1a0'] },
      { no:62, title:'RAG 평가와 개선의 모든 것 : 데이터셋 제작부터 agent 평가까지', sub:'AI 모델 개발', year:'2025.01', tools:'RAG', hours:'21시간 51분', sessions:83, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_evaluation', theme:['#0984e3','#74b9ff'] },
      { no:63, title:'MCP와 A2A로 끝내는 상상도 못할 Multi-Agent 구축', sub:'AI 모델 개발', year:'2025.06', tools:'MCP, A2A', hours:'27시간 34분', sessions:99, ai:true, new:true, link:'https://fastcampus.co.kr/data_online_mcpa2a', theme:['#00b894','#55efc4'] },
      { no:64, title:'AI로 한 번에 끝내는 데이터 분석 자동화', sub:'데이터 엔지니어링', year:'2025.10', tools:'Cursor ai, MCP', hours:'12시간 20분', sessions:34, ai:true, new:true, link:'https://fastcampus.co.kr/data_online_cursormcp', theme:['#fdcb6e','#e17055'] },
      { no:65, title:'2025 AI 시대 일잘러를 위한 비즈니스 데이터 분석 by. 데이터리차드', sub:'데이터 엔지니어링', year:'2025.08', tools:'ChatGPT', hours:'14시간 44분', sessions:106, ai:true, new:true, link:'https://fastcampus.co.kr/data_online_richard', theme:['#6c5ce7','#a29bfe'] },
      { no:66, title:'n8n x 데이터 분석 : 원클릭으로 끝내는 데이터 분석 자동화', sub:'데이터 엔지니어링', year:'2025.07', tools:'n8n', hours:'18시간 39분', sessions:59, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_datapopcorn', theme:['#00cec9','#81ecec'] },
      { no:67, title:'AI로 코딩하는 시대! 비개발자도 할 수 있는 Cursor.AI 실전 웹 제작', sub:'데이터 엔지니어링', year:'2025.02', tools:'Cursor ai', hours:'12시간 56분', sessions:58, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_cursor', theme:['#fd79a8','#e84393'] },
      { no:68, title:'데이터로 승부하라! 실패없는 의사결정을 위한 data driven report', sub:'데이터 엔지니어링', year:'2025.01', tools:'ChatGPT', hours:'14시간 21분', sessions:65, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_datadriven', theme:['#e17055','#fab1a0'] },
      { no:69, title:'Figma MCP, Cursor로 1시간만에 만드는 고퀄리티 웹/앱 서비스', sub:'데이터 엔지니어링', year:'2025.06', tools:'Figma MCP, Curso', hours:'13시간 10분', sessions:26, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_figmamcp', theme:['#0984e3','#74b9ff'] },
      { no:70, title:'2025 데이터분석 Master Class', sub:'데이터 엔지니어링', year:'2025.05', tools:'ChatGPT, SQL, Tableau', hours:'91시간 34분', sessions:466, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_datamaster2', theme:['#00b894','#55efc4'] },
      { no:71, title:'노베이스도 일단! 만들면서 시작하는 나만의 AI 서비스 개발 with 필로소피 AI', sub:'데이터 엔지니어링', year:'2025.04', tools:'Cursor, DeepL', hours:'17시간 05분', sessions:60, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_philosophy', theme:['#fdcb6e','#e17055'] },
      { no:72, title:'ROS 2 & Gazebo를 활용한 로봇 모델링과 자율주행 시뮬레이션', sub:'머신러닝/로보틱스', year:'2025.03', tools:'ROS 2, Gazebo', hours:'12시간 39분', sessions:7, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_selfdriving2', theme:['#6c5ce7','#a29bfe'] },
      { no:73, title:'노벨상도 주목하는 AI 신약개발 프로세스', sub:'데이터 엔지니어링', year:'2025.02', tools:'파이썬', hours:'42시간 17분', sessions:188, ai:true, new:false, link:'https://fastcampus.co.kr/data_online_aimprocess', theme:['#00cec9','#81ecec'] },
      { no:74, title:'한 번에 끝내는 LLMOps & 데이터 파이프라인 구축', sub:'데이터 엔지니어링', year:'2025.01', tools:'LLMOps', hours:'33시간 28분', sessions:21, ai:true, new:false, link:'https://fastcampus.co.kr/data_oneonone_llmops', theme:['#fd79a8','#e84393'] },
      { no:75, title:'국내 1티어급 이커머스 플랫폼으로 배우는 대용량 데이터 처리 끝판왕', sub:'데이터 엔지니어링', year:'2025.08', tools:'Kafka & Flink, Spark, Redis', hours:'28시간 55분', sessions:11, ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_ldh', theme:['#e17055','#fab1a0'] },
      { no:76, title:'[직:장인(匠人)] 중학생도 알 수 있는 데이터분석을 위한 통계 : 수학 포기자도 이해할 수 있는 현실 밀착형 데이터 분석 입문', sub:'데이터 엔지니어링', year:'2025.11', tools:'', hours:'5시간 12분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_basicstatistics', theme:['#0984e3','#74b9ff'] },
      { no:77, title:'[직:장인(匠人)] 데이터는 많은데, 왜 결정은 감으로 하나요? : 숫자에서 실행으로 가는 데이터 기반 의사결정의 기술', sub:'데이터 엔지니어링', year:'2025.11', tools:'', hours:'5시간 08분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_actionabledata', theme:['#00b894','#55efc4'] },
      { no:78, title:'[직:장인(匠人)] 팩트로 세우는 영향력 : 데이터와 말하기로 결정을 움직이는 방법', sub:'데이터 엔지니어링', year:'2025.11', tools:'', hours:'5시간 03분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_data_communication', theme:['#fdcb6e','#e17055'] },
    ]
  },
  {
    id: 'prog', label: '💻 프로그래밍', count: 16,
    courses: [
      { no:79, title:'개발자를 위한 MCP의 모든 것 : 개발 환경 자동화부터 비즈니스 로직 구성까지', sub:'AI 코딩/개발', year:'2025.08', tools:'MCP, Claude code', hours:'14시간 41분', sessions:49, ai:true, new:true, link:'https://fastcampus.co.kr/dev_online_devmcp', theme:['#6c5ce7','#a29bfe'] },
      { no:80, title:'바이브코딩 + 자동화 풀 패키지: 21개 프로젝트로 내 인생 자동화 (w. n8n x Claude Code)', sub:'AI 코딩/개발', year:'2025.10', tools:'', hours:'-', ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_vibecodingn8n', theme:['#00cec9','#81ecec'] },
      { no:81, title:'1일 1바이브코딩, 30개 프로젝트 완성! Cursor AI X Claude Code로 돈 버는 웹 & 앱 만들기', sub:'AI 코딩/개발', year:'2025.08', tools:'', hours:'-', ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_vibecoding30', theme:['#fd79a8','#e84393'] },
      { no:82, title:'B-Harvest와 함께 하는 2025 블록체인 개발의 모든 것', sub:'블록체인', year:'2025.02', tools:'', hours:'40시간 16분', sessions:133, ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_bharvest', theme:['#e17055','#fab1a0'] },
      { no:83, title:'외주 개발 바이블 : Cursor AI로 시작하는 프리랜서 실전 패키지', sub:'AI 코딩/개발', year:'2025.06', tools:'Cursor AI', hours:'21시간 17분', sessions:125, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_devfreelance', theme:['#0984e3','#74b9ff'] },
      { no:84, title:'코딩셰프의 Flutter 맛집 : 왕초보도 가능한 5개 앱 개발부터 스토어 등록까지', sub:'프론트/모바일', year:'2025.04', tools:'Flutter', hours:'19시간 43분', sessions:90, ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_codingchef', theme:['#00b894','#55efc4'] },
      { no:85, title:'1티어 패션 커머스의 세일 도메인 프로젝트로 배우는 대규모 트래픽을 견디는 실전 백엔드의 모든 것', sub:'백엔드', year:'2025.07', tools:'kafka, redis', hours:'24시간 12분', sessions:80, ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_mbf', theme:['#fdcb6e','#e17055'] },
      { no:86, title:'대규모 채팅 플랫폼으로 한 번에 끝내는 실전 대용량 트래픽 커버 완전판', sub:'백엔드', year:'2025.03', tools:'Java, Spring', hours:'55시간 29분', sessions:100, ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_chat', theme:['#6c5ce7','#a29bfe'] },
      { no:87, title:'효율적이고 안정적인 iOS 코드 설계 : 함수형 & 선언형 프로그래밍 패러다임', sub:'프론트/모바일', year:'2025.06', tools:'Xcode 16, Swift 6.0', hours:'6시간 55분', ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_functional', theme:['#00cec9','#81ecec'] },
      { no:88, title:'강민철의 인공지능 시대 필수 컴퓨터 공학 지식', sub:'코딩 입문', year:'2025.03', tools:'', hours:'35시간 51분', sessions:129, ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_kmc', theme:['#fd79a8','#e84393'] },
      { no:89, title:'코딩 초보도 가능한 AI 활용 13가지 프로젝트 with 투더제이', sub:'AI 코딩/개발', year:'2025.01', tools:'ChatGPT, 파이썬', hours:'12시간 23분', sessions:63, ai:false, new:false, link:'https://fastcampus.co.kr/dev_online_ttj', theme:['#e17055','#fab1a0'] },
      { no:90, title:'절대 실패하지 않는 무적의 바이브코딩 성공 공식 (w. 100가지 케이스)', sub:'AI 코딩/개발', year:'2025.10', tools:'', hours:'-', sessions:170, ai:true, new:true, link:'https://fastcampus.co.kr/data_online_vibe100', theme:['#0984e3','#74b9ff'] },
      { no:91, title:'LLM 모델 개발부터 4개 프로젝트로 완성하는 도메인 특화 파인튜닝 w.추론', sub:'AI 코딩/개발', year:'2025.06', tools:'', hours:'-', ai:true, new:true, link:'https://fastcampus.co.kr/data_online_domain', theme:['#00b894','#55efc4'] },
      { no:92, title:'AI 시대, 차이를 만드는 추월 공식 = SQL^AI', sub:'AI 코딩/개발', year:'2025.07', tools:'', hours:'-', ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_sqlwai', theme:['#fdcb6e','#e17055'] },
      { no:93, title:'genspark, manus, flowith로 끝내는 AI 에이전트 비법노트 (ft. v0, NotebookLM)', sub:'AI 코딩/개발', year:'2025.09', tools:'', hours:'-', ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_aisink', theme:['#6c5ce7','#a29bfe'] },
      { no:94, title:'개발자에게 배우는 Cursor AI 고급 노하우 : 컨텍스트 엔지니어링 기반 Agent 실무 도입', sub:'AI 코딩/개발', year:'2025.07', tools:'', hours:'-', ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_devcursorai', theme:['#00cec9','#81ecec'] },
    ]
  },
  {
    id: 'mktg', label: '📣 마케팅·기획', count: 22,
    courses: [
      { no:95, title:'이노션 AI 리더 & 1인 기업 대표가 알려주는 24시간 나 대신 일하는 복제 마케터 만들기', sub:'마케팅 전략', year:'2025.09', tools:'n8n, Claude, make', hours:'24시간 18분', sessions:67, ai:true, new:true, link:'https://fastcampus.co.kr/mktg_online_mcpmkt', theme:['#6c5ce7','#a29bfe'] },
      { no:96, title:'시선을 사로잡는 AI 기반 SNS 광고 제작', sub:'콘텐츠 제작', year:'2025.05', tools:'미드저니, freepik', hours:'13시간 32분', sessions:8, ai:true, new:false, link:'https://fastcampus.co.kr/dgn_online_shortform', theme:['#00cec9','#81ecec'] },
      { no:97, title:'2025 한 번에 끝내는 디지털 마케팅 초격차 패키지 : signature plus', sub:'퍼포먼스 마케팅', year:'2025.02', tools:'미드저니, 어도비, 피그마', hours:'210시간 25분', sessions:778, ai:true, new:true, link:'https://fastcampus.co.kr/mktg_online_digitmktg', theme:['#fd79a8','#e84393'] },
      { no:98, title:'셀피쉬클럽 젬마의 AI 풀스택 마케팅팀 구현 : 10인 규모의 AI 마케팅팀', sub:'퍼포먼스 마케팅', year:'2025.01', tools:'ChatGPT, 캔바, Perplexity', hours:'18시간 09분', sessions:10, ai:true, new:false, link:'https://fastcampus.co.kr/mktg_online_zemma', theme:['#e17055','#fab1a0'] },
      { no:99, title:'[직:장인(匠人)] 0원으로 매출 만드는 논페이드 마케팅 실행 매뉴얼', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'6시간 24분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_nonpaidmanual', theme:['#0984e3','#74b9ff'] },
      { no:100, title:'마케터가 아닌 당신을 위한 생존 마케팅 : 외주 없이, 10일 만에 고객을 부르는 콘텐츠 전략', sub:'고객전략', year:'2025.06', tools:'ChatGPT, 미드저니, make', hours:'18시간 42분', sessions:78, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_nonmarketer', theme:['#00b894','#55efc4'] },
      { no:101, title:'[직:장인(匠人)] 고객이 답이다 : 비즈니스 성과를 만드는 고객 전략의 모든 것', sub:'고객전략', year:'2025.11', tools:'', hours:'5시간 36분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_customerinsightstrategy', theme:['#fdcb6e','#e17055'] },
      { no:102, title:'[직:장인(匠人)] 후킹이란 놈을 처음부터 다시 배워봤습니다 : 메시지가 안 박힐 때 꺼내보는 카피 작성 매뉴얼', sub:'카피라이팅', year:'2025.11', tools:'', hours:'5시간 27분', sessions:60, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_hookingcopy', theme:['#6c5ce7','#a29bfe'] },
      { no:103, title:'[직:장인(匠人)] 보이지 않는 걸 파는 법 : 교육, SaaS, 서비스 등 무형 상품의 마케팅 방법', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'5시간 19분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_intangiblesales', theme:['#00cec9','#81ecec'] },
      { no:104, title:'[직:장인(匠人)] 브랜드 인상학 : 첫 문장·첫 장면·첫 감정으로 각인되는 전략', sub:'브랜딩', year:'2025.11', tools:'', hours:'5시간 10분', sessions:99, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_sensorybranding', theme:['#fd79a8','#e84393'] },
      { no:105, title:'[직:장인(匠人)] 프로모션, 할인 말고 다른 거 없나요? : 실무 마케터를 위한 명분 있는 프로모션 기획 가이드', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'5시간 09분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_promotionplanning', theme:['#e17055','#fab1a0'] },
      { no:106, title:'[직:장인(匠人)] Retention 매커니즘 : 사용자가 떠나지 않는 경험 설계의 기술', sub:'고객전략', year:'2025.11', tools:'', hours:'5시간 07분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_retentionmechanism', theme:['#0984e3','#74b9ff'] },
      { no:107, title:'[직:장인(匠人)] 마케팅은 몰라도 마케터랑은 일해야 하잖아 : 프로덕트·디자인·기획팀이 꼭 알아야 할 마케팅 팀의 관점', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'5시간 07분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_marketingmindset', theme:['#00b894','#55efc4'] },
      { no:108, title:'[직:장인(匠人)] 속마음까지 훔쳐라 : 마케팅부터 제품까지, 페르소나 하나로 설계하는 비즈니스', sub:'고객전략', year:'2025.11', tools:'', hours:'5시간 07분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_emotiondrivenpersona', theme:['#fdcb6e','#e17055'] },
      { no:109, title:'[직:장인(匠人)] 제품보다 먼저 검증하는 초기 고객 확보 전략 50가지 : 신사업 기획자와 스타트업 팀을 위한 시장 진입 가이드', sub:'고객전략', year:'2025.11', tools:'', hours:'5시간 07분', sessions:51, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_customeracquisition', theme:['#6c5ce7','#a29bfe'] },
      { no:110, title:'[직:장인(匠人)] 마케팅 타이밍 : 고객 심리를 열어주는 결정적 순간', sub:'고객전략', year:'2025.11', tools:'', hours:'4시간 58분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_marketingtiming', theme:['#00cec9','#81ecec'] },
      { no:111, title:'The RED : 이케아 서기석 CMO의 브랜드 혁신 15가지 마케팅 전략 원칙', sub:'브랜딩', year:'2025.03', tools:'', hours:'27시간 44분', sessions:13, ai:false, new:false, link:'https://fastcampus.co.kr/mktg_red_brand15', theme:['#fd79a8','#e84393'] },
      { no:112, title:'[직:장인(匠人)] 인사팀 입사 전략서 : 로망은 내려놓고 현실만 챙긴 10가지 전략', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'5시간 42분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_hrentrystrategy', theme:['#e17055','#fab1a0'] },
      { no:113, title:'[직:장인(匠人)] 기획은 바둑, 보고는 한 수 앞 읽기다 : 반론을 잠재우는 예측형 커뮤니케이션', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'5시간 09분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_persuasionflow', theme:['#0984e3','#74b9ff'] },
      { no:114, title:'[직:장인(匠人)] 내가 노력한걸, 고객이 알아줬으면 좋겠어 : 공급자 관점에서 고객 관점으로 바꾸는 언어 기술', sub:'고객전략', year:'2025.11', tools:'', hours:'5시간 01분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_customercentriccopy', theme:['#00b894','#55efc4'] },
      { no:115, title:'[직:장인(匠人)] 자꾸 낮아지는 직장인 문해력 향상법 : 잘 읽고, 잘 쓰는 일잘러의 기본기', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'4시간 59분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_businesswriting', theme:['#fdcb6e','#e17055'] },
      { no:116, title:'[직:장인(匠人)] 회사에서는 이렇게 말하고, 이렇게 씁니다 : 당당하지만 안 밉고, 솔직하지만 안 무례한 사람들의 표현법', sub:'마케팅 전략', year:'2025.11', tools:'', hours:'4시간 59분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_businesscommunication', theme:['#6c5ce7','#a29bfe'] },
    ]
  },
  {
    id: 'career', label: '🏆 커리어·리더십', count: 147,
    courses: [
      { no:117, title:'바이브코딩 입문자를 위한 필수 조합 : 구글 안티그래비티 × 클로드코드 15개 실전 프로젝트', sub:'업무역량', year:'2026.05', tools:'', hours:'16시간 59분', ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_gwonvibe', theme:['#6c5ce7','#a29bfe'] },
      { no:118, title:'연구자를 위한 Gemini 바이블 : 연구 빈틈 포착부터 논문 작성까지 w. Zotero, Obsidian', sub:'업무역량', year:'2025.11', tools:'Gemini, Zotero, Obsidian', hours:'17시간 41분', sessions:58, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_geminibible', theme:['#00cec9','#81ecec'] },
      { no:119, title:'예과생부터 펠로우까지, 성공하는 의사를 위한 의학 연구 방법', sub:'업무역량', year:'2025.05', tools:'ChatGPT', hours:'5시간 48분', sessions:4, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_medres2', theme:['#fd79a8','#e84393'] },
      { no:120, title:'가방끈 커뮤니티 클로이의 연구자를 위한 ChatGPT 및 AI 200% 활용법', sub:'업무역량', year:'2025.02', tools:'ChatGPT', hours:'6시간 10분', sessions:5, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_graduate', theme:['#e17055','#fab1a0'] },
      { no:121, title:'세계 3대 컨설팅펌 출신 김영롱에게 배우는 1조 가치 보고서 작성법', sub:'OA/문서작성', year:'2025.08', tools:'OA', hours:'11시간 20분', sessions:7, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_bestreport', theme:['#0984e3','#74b9ff'] },
      { no:122, title:'2025 페이퍼로지의 이기는 PPT with AI', sub:'OA/문서작성', year:'2025.04', tools:'미드저니, PPT', hours:'15시간 32분', sessions:41, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_winppt', theme:['#00b894','#55efc4'] },
      { no:123, title:'ChatGPT와 무작정 풀어보는 공여사의 엑셀실무', sub:'OA/문서작성', year:'2025.07', tools:'ChatGPT', hours:'10시간 49분', sessions:50, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_gongchatgpt', theme:['#fdcb6e','#e17055'] },
      { no:124, title:'차원이 다른 연구 프로세스 : 연구자를 위한 AI툴 활용법', sub:'업무역량', year:'2025.08', tools:'ChatGPT', hours:'15시간 45분', sessions:52, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_researcher', theme:['#6c5ce7','#a29bfe'] },
      { no:125, title:'의사에게 배우는 ChatGPT 의학 연구방법', sub:'업무역량', year:'2025.02', tools:'ChatGPT', hours:'7시간 49분', sessions:9, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_doctorgpt', theme:['#00cec9','#81ecec'] },
      { no:126, title:'100억을 움직이는 50가지 PPT 디자인 원칙', sub:'OA/문서작성', year:'2025.07', tools:'PPT', hours:'10시간 09분', sessions:5, ai:false, new:false, link:'https://fastcampus.co.kr/biz_online_ppt50', theme:['#fd79a8','#e84393'] },
      { no:127, title:'온보딩 없이 바로 실무 투입! 회사에서 신뢰받는 일센스 만렙 신입되기', sub:'OA/문서작성', year:'2025.01', tools:'OA', hours:'32시간 43분', sessions:17, ai:false, new:false, link:'https://fastcampus.co.kr/biz_online_newbieskill', theme:['#e17055','#fab1a0'] },
      { no:128, title:'[직:장인(匠人)] 비즈니스 그로스 해킹 : 사람은 늘었는데 왜 성장은 느려졌을까?', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 50분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_orggrowthhacking', theme:['#0984e3','#74b9ff'] },
      { no:129, title:'[직:장인(匠人)] 노트북 하나로 시작하는 마켓리서치 : 검색창 하나로 시작하는 시장조사의 모든 것', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 18분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_deskresearchgoogle', theme:['#00b894','#55efc4'] },
      { no:130, title:'[직:장인(匠人)] 익숙한 방식으로, 낯선 시장을 만나는 법 : 리소스는 그대로, 고객만 바꾸는 복합 확장 전략', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 15분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_structuralexpansion', theme:['#fdcb6e','#e17055'] },
      { no:131, title:'[직:장인(匠人)] 고객 검증의 기술 : 시장에서 살아남는 상품 만들기', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 57분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_customerverification', theme:['#6c5ce7','#a29bfe'] },
      { no:132, title:'[직:장인(匠人)] 잠재고객 계산법 : 브랜딩보다 먼저 해야 할, 시장을 숫자로 설계하는 사고법', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 56분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_potentialcustomer', theme:['#00cec9','#81ecec'] },
      { no:133, title:'[직:장인(匠人)] 존재 브랜딩 : 반복 가능한 실력에서, 대체 불가능한 존재로', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 56분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_existencebranding', theme:['#fd79a8','#e84393'] },
      { no:134, title:'[직:장인(匠人)] 비싸도 사게, 싸도 고급스럽게 : 가격 저항을 기회로 바꾸는 브랜드 언어', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 48분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_behavioraldesign', theme:['#e17055','#fab1a0'] },
      { no:135, title:'엘트라바이 소희의 공간 장식 마스터클래스 : 디자인부터 제안서까지', sub:'업무역량', year:'2025.03', tools:'', hours:'8시간 38분', sessions:4, ai:false, new:false, link:'https://fastcampus.co.kr/ent_online_sohee', theme:['#0984e3','#74b9ff'] },
      { no:136, title:'부케 장인 소피토씨에게 배우는 웨딩 부케의 모든 것', sub:'업무역량', year:'2025.01', tools:'', hours:'10시간 17분', sessions:7, ai:false, new:false, link:'https://fastcampus.co.kr/ent_online_soffitto', theme:['#00b894','#55efc4'] },
      { no:137, title:'[직:장인(匠人)] 오늘을 설명할 수 있다면, 괜찮은 하루였다 : 사라지지 않게 쌓이는 일의 기록법', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 00분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_dailyrecord', theme:['#fdcb6e','#e17055'] },
      { no:138, title:'심오피스와 함께하는 MZ에게 사랑받는 리더 되는법', sub:'리더십/조직관리', year:'2025.08', tools:'', hours:'9시간 08분', sessions:8, ai:false, new:false, link:'https://fastcampus.co.kr/biz_online_symoffice', theme:['#6c5ce7','#a29bfe'] },
      { no:139, title:'[직:장인(匠人)] 경력직을 위한 진로 상담서', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 26분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_careerrebuilding', theme:['#00cec9','#81ecec'] },
      { no:140, title:'[직:장인(匠人)] 그래도 대감 집이 낫지 않을까? : 3년차 이하 직장인의 대기업 현실 이직 가이드', sub:'커리어 성장', year:'2025.11', tools:'', hours:'5시간 24분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_bigcorptransition', theme:['#fd79a8','#e84393'] },
      { no:141, title:'[직:장인(匠人)] 일잘러를 위한 커리어 가이드북 : 조직의 공기를 읽고 흐름을 만드는 사람이 되는 법', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'5시간 00분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_highperformer', theme:['#e17055','#fab1a0'] },
      { no:142, title:'AI로 나만의 영어공부 만드는 꿀잼꿀팁(2)', sub:'업무역량', year:'2024.01', tools:'', hours:'1시간 19분', ai:true, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:143, title:'AI로 나만의 영어공부 만드는 꿀잼꿀팁(1)', sub:'업무역량', year:'2024.01', tools:'', hours:'1시간 10분', ai:true, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:144, title:'AI 퍼스트 시대에 필요한 질문 전략(좋은 질문이 좋은 답을 만든다: 질문의 기술 기초)', sub:'업무역량', year:'2024.01', tools:'', hours:'42분', ai:true, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:145, title:'AI 퍼스트 시대에 필요한 질문 전략(질문의 힘: 논리와 창의력을 키우는 질문법)', sub:'업무역량', year:'2024.01', tools:'', hours:'42분', ai:true, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:146, title:'[직:장인(匠人)] 당신이 몰랐던 실패의 알고리즘 : 의사결정자를 위한 판단 실패 감지 시스템', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 28분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_decisionsignal', theme:['#00cec9','#81ecec'] },
      { no:147, title:'[직:장인(匠人)] 사업개발자입니다. 그런데 제가 뭘 했냐고요? : 당신이 그려놓은 밑그림, 지금부터 말로 증명해보자', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 26분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_bdpositioning', theme:['#fd79a8','#e84393'] },
      { no:148, title:'[직:장인(匠人)] 성과평가를 위한 구조화된 회고와 전략 설계 : 실무자가 반드시 알아야 할 회고-기획 연결 구조', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 25분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_structuredretrospective', theme:['#e17055','#fab1a0'] },
      { no:149, title:'[직:장인(匠人)] 70점의 기술 : 완벽주의 대신 두배의 성과를 만드는 기술', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 21분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_ruleofoutput', theme:['#0984e3','#74b9ff'] },
      { no:150, title:'[직:장인(匠人)] 기억 점유율로 설계하는 브랜딩 : 포화된 시장에서 살아남는 브랜드를 만드는 구조적 사고', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 20분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_memorybranding', theme:['#00b894','#55efc4'] },
      { no:151, title:'[직:장인(匠人)] 해내는 조직 : 예측 가능한 지연을 제어하는 프로젝트 관리법', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'5시간 11분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_decisiondrivenschedule', theme:['#fdcb6e','#e17055'] },
      { no:152, title:'[직:장인(匠人)] 잘 파는 사람들의 성공엔 법칙이 있다 : 전설들은 어떻게 판단하고, 결정하는가', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 08분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_relationshipselling', theme:['#6c5ce7','#a29bfe'] },
      { no:153, title:'[직:장인(匠人)] 기획은 질문에서 시작된다 : 문제를 정리하고 실행을 선명하게 만드는 법', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 04분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_questiondrivenplanning', theme:['#00cec9','#81ecec'] },
      { no:154, title:'[직:장인(匠人)] 상위 1%는 답하지 않고, 질문한다. : 생각, 전략, 실행이 성과로 바뀌는 질문의 기술', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 54분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_questiondesign', theme:['#fd79a8','#e84393'] },
      { no:155, title:'[직:장인(匠人)] 구조없는 BM은 반드시 무너진다 : 기획자와 창업자를 위한 전략적 BM 설계 매뉴얼', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 52분', sessions:49, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_businessmodelstructure', theme:['#e17055','#fab1a0'] },
      { no:156, title:'[직:장인(匠人)] 브랜드가 다르게 읽히는 시장에서 살아남는 법 : 당신이 만든 건 ‘무엇’이고, 그들은 그것을 ‘뭐’라고 부를까', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 49분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_marketreadingglobal', theme:['#0984e3','#74b9ff'] },
      { no:157, title:'[직:장인(匠人)] 기억에 남는 한 줄은 이렇게 만들어진다 : 사람들이 기억하고 구매하게 만드는 한줄의 기술', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 36분', sessions:9, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_brandtaglinecopy', theme:['#00b894','#55efc4'] },
      { no:158, title:'[직:장인(匠人)] 사수 없이 레벨업 : 혼자서도 성장하는 직장인의 1년 플랜', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 45분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_selfonboarding', theme:['#fdcb6e','#e17055'] },
      { no:159, title:'[직:장인(匠人)] 창의력의 역설 : 회사에서 창의적으로 일한다는 당신에게 꼭 필요한 ‘모방의 기술’', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 29분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_creativeremix', theme:['#6c5ce7','#a29bfe'] },
      { no:160, title:'[직:장인(匠人)] 커뮤니케이션 밀도 : 프로젝트 성공률을 높이는 언어의 설계', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 25분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_communicationdensity', theme:['#00cec9','#81ecec'] },
      { no:161, title:'[직:장인(匠人)] TAM은 말할 수 있는데, SOM은 설명 못 하겠다면 : 시장 크기가 아니라, 시장 입구를 찾아야 할 때', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 24분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_tamsomstrategy', theme:['#fd79a8','#e84393'] },
      { no:162, title:'[직:장인(匠人)] 시스템으로 만들어내는 리더십 : 글로벌 조직이 택한 ‘보이지 않는 리더’의 일 방식', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'5시간 24분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_systemleadership', theme:['#e17055','#fab1a0'] },
      { no:163, title:'[직:장인(匠人)] 사업개발 처음인데요, 어디서부터 시작하죠? : 실무로 배우는 시장조사, 비즈니스 모델링, 숫자 정리의 모든 것', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 22분', sessions:49, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_businessdevelopment101', theme:['#0984e3','#74b9ff'] },
      { no:164, title:'[직:장인(匠人)] 니즈는 머릿속에 없다.사람에게 있다 : 제품 개발보다 중요한 고객 개발의 기술', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 17분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_customervalidation', theme:['#00b894','#55efc4'] },
      { no:165, title:'[직:장인(匠人)] 관계 비용은 언제나 채용 뒤에 온다 : 우리는 왜 자꾸 ‘불편한 실력자’를 뽑게 될까?', sub:'커리어 성장', year:'2025.11', tools:'', hours:'5시간 15분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_relationshipcost', theme:['#fdcb6e','#e17055'] },
      { no:166, title:'[직:장인(匠人)] 좋은 사람이 아닌, 좋은 팀장이 되고 싶은 신입 팀장 가이드', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'5시간 12분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_newteamlead', theme:['#6c5ce7','#a29bfe'] },
      { no:167, title:'[직:장인(匠人)] 흔들릴지언정, 부서지지 않는다 : 위기 속에서 팀을 단단하게 만드는 회복 전략', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 11분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_teamresilience', theme:['#00cec9','#81ecec'] },
      { no:168, title:'[직:장인(匠人)] 경력 포지셔닝의 기술 : 연차별 성장 속도를 높이는 실전 커리어 매뉴얼', sub:'커리어 성장', year:'2025.11', tools:'', hours:'5시간 10분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_positioning', theme:['#fd79a8','#e84393'] },
      { no:169, title:'[직:장인(匠人)] 위대한 결정의 해부학 : 이기는 선택은 어떻게 만들어지는가', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 09분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_strategicbets', theme:['#e17055','#fab1a0'] },
      { no:170, title:'[직:장인(匠人)] 한 명 더 뽑는 순간, 리더십이 바뀐다 : 조직은 커지는 게 아니라, 나누는 방식이 달라진다', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'5시간 09분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_leadershipgrowth', theme:['#0984e3','#74b9ff'] },
      { no:171, title:'[직:장인(匠人)] 경쟁하지말고, 지배하라 : ‘비교 불가’의 영역을 선점하는 비즈니스 전략', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 08분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_onlyplayerstrategy', theme:['#00b894','#55efc4'] },
      { no:172, title:'[직:장인(匠人)] 번아웃 졸업식 : 일 잘하는 사람이 탈진하는 이유', sub:'자기계발/마인드', year:'2025.11', tools:'', hours:'5시간 07분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_burnoutrecovery', theme:['#fdcb6e','#e17055'] },
      { no:173, title:'[직:장인(匠人)] 중간관리자라는 이름의 이중통역사 : 감정은 삼키고, 말로 조율하는 성장기술', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 07분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_translatorleader', theme:['#6c5ce7','#a29bfe'] },
      { no:174, title:'[직:장인(匠人)] NEED는 말이 없고, WANT는 시끄럽다 : 말보다 행동을, 반응보다 전환을 읽는 관점', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 06분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_behavioranalytics', theme:['#00cec9','#81ecec'] },
      { no:175, title:'[직:장인(匠人)] 회사는 싫지만, 일은 계속해야 하잖아 : 그래서 시작하는 업덕일치', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 05분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_workgamification', theme:['#fd79a8','#e84393'] },
      { no:176, title:'[직:장인(匠人)] 시장 진입의 실전 설계도 : 고객이 아닌 시장을 먼저 설득하는 전략', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 04분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_gtmstrategy', theme:['#e17055','#fab1a0'] },
      { no:177, title:'[직:장인(匠人)] 취향은 변하고, 세계관은 남는다 : 유행보다 믿음을, 반응보다 행동을 읽는 법', sub:'업무역량', year:'2025.11', tools:'', hours:'5시간 03분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_worldview', theme:['#0984e3','#74b9ff'] },
      { no:178, title:'[직:장인(匠人)] 무엇을 하지 않을 것인가 : 자원을 낭비하지 않는 조직의 기준', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'5시간 00분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_focusstrategy', theme:['#00b894','#55efc4'] },
      { no:179, title:'[직:장인(匠人)] 신사업에선 ‘잘하는 사람’도 다시 배운다 : 신사업 팀 첫 출근 가이드', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'5시간 00분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_newbizplaybook', theme:['#fdcb6e','#e17055'] },
      { no:180, title:'[직:장인(匠人)] 무에서 유를 만든 사람들 : 시장에 존재감을 만들어낸 실행 기록', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 58분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_marketsensing', theme:['#6c5ce7','#a29bfe'] },
      { no:181, title:'[직:장인(匠人)] 생각 PT', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 58분', sessions:50, ai:false, new:true, link:null, theme:['#00cec9','#81ecec'] },
      { no:182, title:'[직:장인(匠人)] 직장인에게 필요한 마음연고 : 인문학으로 배우는 지혜로운 회사생활', sub:'자기계발/마인드', year:'2025.11', tools:'', hours:'4시간 58분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_stoicmindfulness', theme:['#fd79a8','#e84393'] },
      { no:183, title:'[직:장인(匠人)] 6개월 앞, 스마일 커브 구간입니다. : 정체를 ‘전환 구간’으로 바꾸는 조직 전략 가이드', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'4시간 57분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_scurve_transition', theme:['#e17055','#fab1a0'] },
      { no:184, title:'[직:장인(匠人)] 소비 설계 : 구매를 일으키는 기획의 사고방식', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 56분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_consumptiondesign', theme:['#0984e3','#74b9ff'] },
      { no:185, title:'[직:장인(匠人)] 조직 포트폴리오 : 말 안 해도 ‘어떤 팀인지’ 보이는 방식', sub:'리더십/조직관리', year:'2025.11', tools:'', hours:'4시간 56분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_orgportfolio', theme:['#00b894','#55efc4'] },
      { no:186, title:'[직:장인(匠人)] 역량론 : 문제해결능력 : 정답이 아닌 기준을 세우는 힘', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 55분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_problem_solving', theme:['#fdcb6e','#e17055'] },
      { no:187, title:'[직:장인(匠人)] 감탄 유도 매뉴얼 : AHA MOMENT를 설계하는 사람들의 각본', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 53분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/dgn_online_ahamoment', theme:['#6c5ce7','#a29bfe'] },
      { no:188, title:'[직:장인(匠人)] 센스는 타고나는 게 아니라, 케이스를 쌓는 것이다', sub:'업무역량', year:'2025.11', tools:'', hours:'4시간 52분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/mktg_online_brandsentence', theme:['#00cec9','#81ecec'] },
      { no:189, title:'[리더십 아카이브] 성과 리더십(평가피드백과 직원육성)', sub:'리더십/조직관리', year:'2025.04', tools:'', hours:'3시간 57분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:190, title:'[리더십 아카이브] 변화 리더십(조직개발과 퍼실리테이션)', sub:'리더십/조직관리', year:'2025.04', tools:'', hours:'3시간 45분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:191, title:'[핵심인재 아카이브] 차세대리더의 업무·관계역량(대리급)', sub:'리더십/조직관리', year:'2025.04', tools:'', hours:'3시간 30분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:192, title:'[Biz 아카이브] 불확실성 시대의 문제해결과 의사결정', sub:'업무역량', year:'2024.01', tools:'', hours:'3시간 58분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:193, title:'에니어그램을 활용한 코칭리더십(2)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'3시간 32분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:194, title:'에니어그램을 활용한 코칭리더십(1)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'3시간 08분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:195, title:'당신의 생각을 정리해드립니다. 디지털 비주얼씽킹(실전: 창의적 표현과 계획)', sub:'업무역량', year:'2024.01', tools:'', hours:'2시간 52분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:196, title:'당신의 생각을 정리해드립니다. 디지털 비주얼씽킹(기초: 시각적 사고의 시작)', sub:'업무역량', year:'2024.01', tools:'', hours:'2시간 33분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:197, title:'목표달성을 위한 성과관리 코칭(1)', sub:'업무역량', year:'2024.01', tools:'', hours:'2시간 27분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:198, title:'목표달성을 위한 성과관리 코칭(2)', sub:'업무역량', year:'2024.01', tools:'', hours:'2시간 11분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:199, title:'몰입과 시너지 높은 고성과 팀, 조직문화로 이끌어라!(조직문화 이해)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'2시간 02분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:200, title:'몰입과 시너지 높은 고성과 팀, 조직문화로 이끌어라!(조직문화 변화)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'1시간 42분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:201, title:'어쩌다 기획자, 초보 IT기획자를 위한 업무노트(1)', sub:'업무역량', year:'2024.01', tools:'', hours:'1시간 29분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:202, title:'이 세상 모든 낀세대 팀장을 위한 360도 팀장 리더십(상사/팀원과의 관계 편)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'1시간 11분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:203, title:'이 세상 모든 낀세대 팀장을 위한 360도 팀장 리더십(동료/자신과의 관계 편)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'1시간 09분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:204, title:'어쩌다 기획자, 초보 IT기획자를 위한 업무노트(2)', sub:'업무역량', year:'2024.01', tools:'', hours:'1시간 05분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:205, title:'칭찬받는 신입사원의 회사생활 매뉴얼', sub:'커리어 성장', year:'2024.01', tools:'', hours:'1시간 05분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:206, title:'행복하게 일하며 능력을 인정받는 조직문화 만들기(조직 소통과 업무 몰입)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'1시간 04분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:207, title:'창의적인 리더를 넘어 성장하는 리더의 조건', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'58분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:208, title:'결국 승리하는 작은 성공의 힘(재능 개발의 과학: 감정, 신념, 실행의 원리)', sub:'업무역량', year:'2024.01', tools:'', hours:'54분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:209, title:'결국 승리하는 작은 성공의 힘(재능의 비밀: 학습과 성장의 과학)', sub:'업무역량', year:'2024.01', tools:'', hours:'50분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:210, title:'행복하게 일하며 능력을 인정받는 조직문화 만들기(성과 중심 조직문화)', sub:'리더십/조직관리', year:'2024.01', tools:'', hours:'49분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:211, title:'트랜드&사례로 배우는 DT시대에 최적화된 조직문화', sub:'리더십/조직관리', year:'2023.12', tools:'', hours:'3시간 41분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:212, title:'[직장로그] 호감을 높이는 조직 내 인간관계 기술', sub:'리더십/조직관리', year:'2023.12', tools:'', hours:'1시간 44분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:213, title:'[직장로그] 좋은 관계를 유지하는 대화', sub:'업무역량', year:'2023.12', tools:'', hours:'1시간 39분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:214, title:'DT시대를 맞이하는 변혁적 조직관리 리더십', sub:'리더십/조직관리', year:'2023.11', tools:'', hours:'1시간 00분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:215, title:'성장하는 조직의 성과관리, OKR', sub:'리더십/조직관리', year:'2022.01', tools:'', hours:'1시간 32분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:216, title:'[포스트 코로나] 변화관리 리더십', sub:'리더십/조직관리', year:'2022.01', tools:'', hours:'1시간 18분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:217, title:'리더십의 고전, 사마천 사기를 읽다(진·한 교체기의 역사)', sub:'리더십/조직관리', year:'2022.01', tools:'', hours:'1시간 05분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:218, title:'품격을 높여주는 이미지 컨설팅(리더의 이미지와 스타일)', sub:'리더십/조직관리', year:'2022.01', tools:'', hours:'1시간 01분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:219, title:'품격을 높여주는 이미지 컨설팅(이미지와 첫인상)', sub:'업무역량', year:'2022.01', tools:'', hours:'51분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:220, title:'리더십의 고전, 사마천 사기를 읽다(중국사와 역사서)', sub:'리더십/조직관리', year:'2022.01', tools:'', hours:'35분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:221, title:'미래조직과 디지털 리더십', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'3시간 59분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:222, title:'성과관리 리더십(성과관리와 피드백 전략)', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'3시간 46분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:223, title:'성과관리 리더십(실전)', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'3시간 40분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:224, title:'우리의 멘토링(Wementoring)', sub:'업무역량', year:'2021.11', tools:'', hours:'3시간 37분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:225, title:'팀시너지를 만드는 리더의 소통법', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'3시간 28분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:226, title:'인간관계 잘하고 싶은 직장인을 위한 꿀팁! 욕구와 갈등 관리', sub:'업무역량', year:'2021.11', tools:'', hours:'1시간 37분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:227, title:'인간관계 잘하고 싶은 직장인을 위한 꿀팁! 욕구를 통한 관계와 행복', sub:'업무역량', year:'2021.11', tools:'', hours:'1시간 28분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:228, title:'일하는 사람이 행복한 워라밸 리더십(지속 가능한 팀 빌딩과 리더십)', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'1시간 17분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:229, title:'고성과 조직 관리를 위한 팀장 걱정 버리기 6가지 스킬', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'1시간 15분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:230, title:'일하는 사람이 행복한 워라밸 리더십(성공적인 리더십과 팀 성장)', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'1시간 12분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:231, title:'[How-to 성과관리] 팀장을 위한 성과관리 코칭(팀장의 성과관리 원칙)', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'1시간 04분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:232, title:'[How-to 성과관리] 임원을 위한 성과관리 코칭(목표 설정과 자원 배분 전략)', sub:'업무역량', year:'2021.11', tools:'', hours:'1시간 02분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:233, title:'[How-to 성과관리] 팀원을 위한 성과관리 코칭(성과관리 전략)', sub:'업무역량', year:'2021.11', tools:'', hours:'58분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:234, title:'[How-to 성과관리] 팀원을 위한 성과관리 코칭(조직 소통)', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'57분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:235, title:'[How-to 성과관리] 팀장을 위한 성과관리 코칭(전략적 성과관리)', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'56분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:236, title:'[How-to 성과관리] 임원을 위한 성과관리 코칭(임원의 역할과 성과관리)', sub:'업무역량', year:'2021.11', tools:'', hours:'55분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:237, title:'고성과 조직 관리를 위한 팀장 걱정 버리기 4가지 스킬', sub:'리더십/조직관리', year:'2021.11', tools:'', hours:'48분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:238, title:'[How-to 성과관리] 주간 성과관리 방법', sub:'업무역량', year:'2021.01', tools:'', hours:'1시간 05분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:239, title:'슬기로운 직장예절 - 신입사원편', sub:'커리어 성장', year:'2021.01', tools:'', hours:'46분', ai:false, new:false, link:null, theme:['#e17055','#fab1a0'] },
      { no:240, title:'그림책으로 보는 리더십', sub:'리더십/조직관리', year:'2021.01', tools:'', hours:'44분', ai:false, new:false, link:null, theme:['#0984e3','#74b9ff'] },
      { no:241, title:'슬기로운 직장예절 - 선배직원편', sub:'업무역량', year:'2021.01', tools:'', hours:'44분', ai:false, new:false, link:null, theme:['#00b894','#55efc4'] },
      { no:242, title:'슬기로운 직장예절 - 리더편', sub:'리더십/조직관리', year:'2021.01', tools:'', hours:'39분', ai:false, new:false, link:null, theme:['#fdcb6e','#e17055'] },
      { no:243, title:'1%의 핵심인재를 내 사람으로 만드는 조조 리더십(2)', sub:'리더십/조직관리', year:'2019.01', tools:'', hours:'3시간 50분', ai:false, new:false, link:null, theme:['#6c5ce7','#a29bfe'] },
      { no:244, title:'1%의 핵심인재를 내 사람으로 만드는 조조 리더십(3)', sub:'리더십/조직관리', year:'2019.01', tools:'', hours:'3시간 20분', ai:false, new:false, link:null, theme:['#00cec9','#81ecec'] },
      { no:245, title:'1%의 핵심인재를 내 사람으로 만드는 조조 리더십(1)', sub:'리더십/조직관리', year:'2019.01', tools:'', hours:'3시간 00분', ai:false, new:false, link:null, theme:['#fd79a8','#e84393'] },
      { no:246, title:'차원이 다른 기획 프로세스 : 10가지 AI 툴로 끝내는 일잘러 PM 가이드', sub:'기획/전략', year:'2025.05', tools:'ChatGPT, Genspark', hours:'18시간 22분', sessions:59, ai:true, new:true, link:'https://fastcampus.co.kr/biz_online_service', theme:['#e17055','#fab1a0'] },
      { no:247, title:'2025 서비스기획/PM/PO 초격차 패키지 Signature', sub:'기획/전략', year:'2025.04', tools:'ChatGPT, 피그마', hours:'53시간 34분', sessions:230, ai:true, new:false, link:'https://fastcampus.co.kr/biz_online_newpmpo', theme:['#0984e3','#74b9ff'] },
      { no:248, title:'[직:장인(匠人)] 연봉을 높이는 경력기술서 작성 입문 : 무엇을 어떻게 얼마나 써야 할지 고민되는 경력기술서 작성법', sub:'기획/전략', year:'2025.11', tools:'', hours:'5시간 20분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_salaryresume', theme:['#00b894','#55efc4'] },
      { no:249, title:'[직:장인(匠人)] 벤치마킹은 Ctrl+C가 아니라 Ctrl+F다 : 경쟁사 성공사례를 전략으로 바꾸는 PM/PO의 체크리스트', sub:'기획/전략', year:'2025.11', tools:'', hours:'5시간 16분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_benchmarkstrategy', theme:['#fdcb6e','#e17055'] },
      { no:250, title:'[직:장인(匠人)] 제품 기반 성장 : 광고 없이 고객을 붙잡는 전략', sub:'기획/전략', year:'2025.11', tools:'', hours:'5시간 02분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_productledgrowth', theme:['#6c5ce7','#a29bfe'] },
      { no:251, title:'[직:장인(匠人)] 전략은 답이 아니라, 질문으로 만든다 : PM·기획자·브랜드 담당자를 위한 질문 설계 기술', sub:'기획/전략', year:'2025.11', tools:'', hours:'4시간 54분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_strategicquestioningg', theme:['#00cec9','#81ecec'] },
      { no:252, title:'[직:장인(匠人)] 말하지 않는 퇴사 이유에서 찾는 인사 전략 : 떠난 사람의 \'말\'이 아니라 \'흔적\'에서 답을 찾는 현실 인사 가이드', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 30분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_exitsignalplaybook', theme:['#fd79a8','#e84393'] },
      { no:253, title:'[직:장인(匠人)] 채용 언어 매뉴얼 : 선택받는 회사를 만드는 채용 브랜딩 전략', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 16분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_hiringlanguage', theme:['#e17055','#fab1a0'] },
      { no:254, title:'[직:장인(匠人)] 복도의 말이 곧 조직의 말이다 : 인사담당자가 놓친 조직의 진짜 속마음', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 13분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_orgculturelanguage', theme:['#0984e3','#74b9ff'] },
      { no:255, title:'[직:장인(匠人)] 초보 팀장을 위한 관계·성과·커리어 관리 A to Z : 현명한 중간 관리자의 처세술 100가지', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 38분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_newmanagerplaybook', theme:['#00b894','#55efc4'] },
      { no:256, title:'[직:장인(匠人)] 3명이 30명을 이긴다 : 작고 강한 팀 만드는 법', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 37분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_smallteamops', theme:['#fdcb6e','#e17055'] },
      { no:257, title:'[직:장인(匠人)] 또 시작됐다, 갑자기 든 생각 : P 상사 밑에서 일하는 J 회사원의 실무 가이드', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 24분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_psupervisorplaybook', theme:['#6c5ce7','#a29bfe'] },
      { no:258, title:'[직:장인(匠人)] 공기까지 리드하는 리더십 : 실행력을 좌우하는 리더십의 언어 설계', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 13분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_leadershiplanguage', theme:['#00cec9','#81ecec'] },
      { no:259, title:'[직:장인(匠人)] 늘 새로운 걸 원하는 팀장 밑에서 살아남는 법 : 아이디어가 안 떠오르는 날에도 살아남는 실전 생존 기술 50가지', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 12분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_ideationsurvival', theme:['#fd79a8','#e84393'] },
      { no:260, title:'[직:장인(匠人)] 팔로우십이 없으면 리더십도 없다 : 리더가 믿는 실무자의 조건', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 12분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_followership', theme:['#e17055','#fab1a0'] },
      { no:261, title:'[직:장인(匠人)] 리더의 말격(格) : 착한 사람을 넘어 단단한 리더로 성장하는 법', sub:'인사/HR', year:'2025.11', tools:'', hours:'5시간 07분', sessions:10, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_leadershiplanguage2', theme:['#0984e3','#74b9ff'] },
      { no:262, title:'클릭 한번에 완성되는 200가지 이미지: 제품, SNS 브랜딩, 광고 소재까지 w 나노바나나', sub:'업무역량', year:'2026.05', tools:'', hours:'24시간 28분', ai:true, new:true, link:'https://fastcampus.co.kr/dgn_online_bananamix', theme:['#00b894','#55efc4'] },
      { no:263, title:'2026 AI 영상 마스터 클래스: 광고·콘텐츠·숏폼까지 무한 확장', sub:'업무역량', year:'2026.05', tools:'', hours:'41시간 49분', ai:true, new:true, link:'https://fastcampus.co.kr/dgn_online_aiall', theme:['#fdcb6e','#e17055'] },
    ]
  },
  {
    id: 'finance', label: '💰 금융·재테크', count: 9,
    courses: [
      { no:264, title:'15년차 회계사한테 배우는 ChatGPT 기업 분석 & 실전 투자', sub:'회계/재무/세무', year:'2025.04', tools:'ChatGPT', hours:'10시간 32분', sessions:39, ai:true, new:false, link:'https://fastcampus.co.kr/fin_online_si_gpt', theme:['#6c5ce7','#a29bfe'] },
      { no:265, title:'[직:장인(匠人)] 재무제표, 필요한 만큼만 빠르게 읽는 방법 : 비전공 실무자를 위한, 판단 중심 기업 분석', sub:'회계/재무/세무', year:'2025.11', tools:'', hours:'5시간 18분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/fin_online_financialstatementfornonmajors', theme:['#00cec9','#81ecec'] },
      { no:266, title:'[직:장인(匠人)] 버는 만큼 쓰는 팀의 딜레마 : 적자도 수익도 아닌, 생존을 위한 설계', sub:'금융/투자 실무', year:'2025.11', tools:'', hours:'5시간 14분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/fin_online_survivalfinance', theme:['#fd79a8','#e84393'] },
      { no:267, title:'[직:장인(匠人)] 숫자 위의 리더십, 재무경영 : 숫자로 전략을 설계하는 사람의 사고법', sub:'금융/투자 실무', year:'2025.11', tools:'', hours:'5시간 11분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/fin_online_financialleadership', theme:['#e17055','#fab1a0'] },
      { no:268, title:'파이낸셜 모델링 플레이북 : 실무에서 바로 쓰는 산업별 데이터 기반의 밸류에이션 프로젝트', sub:'금융/투자 실무', year:'2025.04', tools:'파이썬', hours:'110시간 27분', sessions:293, ai:false, new:false, link:'https://fastcampus.co.kr/fin_online_pbfinancialmodeling', theme:['#0984e3','#74b9ff'] },
      { no:269, title:'[직:장인(匠人)] 계약서엔 있었는데, 통장엔 없더라고요 : 계약부터 행사까지, 스톡옵션에서 꼭 묻고 따져야 할 조건들', sub:'금융/투자 실무', year:'2025.11', tools:'', hours:'5시간 30분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/fin_online_equitycomp', theme:['#00b894','#55efc4'] },
      { no:270, title:'[직:장인(匠人)] 갭이어 재무설계 : 잠깐의 쉼을 위한 경제적 준비', sub:'금융/투자 실무', year:'2025.11', tools:'', hours:'5시간 19분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/fin_online_gapyearfinance', theme:['#fdcb6e','#e17055'] },
      { no:271, title:'[직:장인(匠人)] 1인사업자의 세무 루틴 만들기 : 내 사업에 맞는 절세와 리스크 관리', sub:'회계/재무/세무', year:'2025.11', tools:'', hours:'5시간 16분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/fin_online_taxroutine', theme:['#6c5ce7','#a29bfe'] },
      { no:272, title:'크립토퀀트 연구원 박별의 온체인 데이터 분석과 투자 전략', sub:'재테크/투자', year:'2025.04', tools:'', hours:'10시간 31분', sessions:5, ai:false, new:false, link:'https://fastcampus.co.kr/fin_online_onchaindata', theme:['#00cec9','#81ecec'] },
    ]
  },
  {
    id: 'lang', label: '🌐 외국어', count: 7,
    courses: [
      { no:273, title:'[직:장인(匠人)] 단어만 있어도 말할 수 있는 영어 회화 템플릿 : 동사, 명사 하나로 시작하는 회화 근육 트레이닝', sub:'영어', year:'2025.11', tools:'', hours:'4시간 57분', sessions:50, ai:false, new:true, link:'https://fastcampus.co.kr/biz_online_wordtosentence', theme:['#6c5ce7','#a29bfe'] },
      { no:274, title:'왕초보의 영어 입문기! 가벼운 영어 기초', sub:'영어', year:'2021.07', tools:'', hours:'4시간 58분', sessions:20, ai:false, new:true, link:null, theme:['#00cec9','#81ecec'] },
      { no:275, title:'MZ세대의 찐- 회화 따라잡기! TPO 특강', sub:'영어', year:'2021.07', tools:'', hours:'2시간 28분', sessions:20, ai:false, new:true, link:null, theme:['#fd79a8','#e84393'] },
      { no:276, title:'2주만에 완성하는! 비즈니스 영어 이메일편', sub:'영어', year:'2021.07', tools:'', hours:'1시간 54분', sessions:30, ai:false, new:true, link:null, theme:['#e17055','#fab1a0'] },
      { no:277, title:'원어민과 함께 배우는! 착 붙는 영어 발음', sub:'영어', year:'2021.07', tools:'', hours:'1시간 49분', sessions:20, ai:false, new:true, link:null, theme:['#0984e3','#74b9ff'] },
      { no:278, title:'콩글리쉬를 교정하라! 영어 발음 교정 특강', sub:'영어', year:'2021.07', tools:'', hours:'1시간 18분', sessions:20, ai:false, new:true, link:null, theme:['#00b894','#55efc4'] },
      { no:279, title:'5분이면 된다! 프레스캇 & 쉐리와 함께하는 5분 영어', sub:'영어', year:'2021.07', tools:'', hours:'1시간 08분', sessions:20, ai:false, new:true, link:null, theme:['#fdcb6e','#e17055'] },
    ]
  },
];

// SVG thumbnail generator
function makeThumbnail(course) {
  const [c1, c2] = course.theme;
  const lines = (course.title.match(/.{1,22}/g) || [course.title]).map(l => l.trim());
  const snippet = lines.slice(0, 2);
  if (lines.length > 2) snippet[1] = snippet[1].replace(/.{1,3}$/, '…');
  const shapes = [
    `<circle cx="240" cy="90" r="70" fill="${c1}" opacity="0.25"/>`,
    `<rect x="0" y="85" width="320" height="1" stroke="${c2}" stroke-width="0.5" opacity="0.3"/>`,
    `<circle cx="30" cy="30" r="40" fill="${c2}" opacity="0.12"/>`,
  ];
  const textLines = snippet.map((t, i) =>
    `<text x="20" y="${65 + i * 22}" font-family="'Pretendard','Apple SD Gothic Neo',sans-serif" font-size="13.5" font-weight="700" fill="white" opacity="0.95">${escapeXml(t)}</text>`
  ).join('');
  return `<svg class="card-thumb-svg" viewBox="0 0 320 180" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="g${course.no}" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" style="stop-color:${c1};stop-opacity:1"/>
        <stop offset="100%" style="stop-color:${c2};stop-opacity:0.7"/>
      </linearGradient>
    </defs>
    <rect width="320" height="180" fill="url(#g${course.no})"/>
    ${shapes.join('')}
    ${textLines}
    <text x="20" y="162" font-family="'Pretendard','Apple SD Gothic Neo',sans-serif" font-size="11" fill="white" opacity="0.6">${escapeXml(course.sub)}</text>
  </svg>`;
}

function escapeXml(str) {
  return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

function makeCard(course) {
  const badges = [
    `<span class="badge badge-sub">${course.sub}</span>`,
    course.ai ? `<span class="badge badge-ai">🤖 AI활용</span>` : '',
    course.new ? `<span class="badge badge-new">🆕 신규</span>` : '',
  ].join('');
  const tag = course.link ? 'a' : 'div';
  const attrs = course.link
    ? ` href="${course.link}" target="_blank" rel="noopener"`
    : '';
  const cardClass = course.link ? 'card' : 'card card-nolink';
  return `<${tag} class="${cardClass}"${attrs}>
    <div class="card-thumb">${makeThumbnail(course)}</div>
    <div class="card-body">
      <div class="card-badges">${badges}</div>
      <div class="card-title">${course.title}</div>
      <div class="card-meta">
        <span class="card-meta-item">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
          ${course.hours}
        </span>
        <span class="card-meta-item">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M8 6h13M8 12h13M8 18h13M3 6h.01M3 12h.01M3 18h.01"/></svg>
          ${course.sessions ? course.sessions + '강' : '-'}
        </span>
        <span class="card-meta-item">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M15 22v-4a4.8 4.8 0 00-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.403 5.403 0 004 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65-.17.6-.22 1.23-.15 1.85v4"/></svg>
          ${course.year || '-'} 개발
        </span>
        <span class="card-meta-item">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14.7 6.3a1 1 0 000 1.4l1.6 1.6a1 1 0 001.4 0l3.77-3.77a6 6 0 01-7.94 7.94l-6.91 6.91a2.12 2.12 0 01-3-3l6.91-6.91a6 6 0 017.94-7.94l-3.76 3.76z"/></svg>
          ${course.tools || '-'}
        </span>
      </div>
    </div>
  </${tag}>`;
}

// Build DOM
const tabsEl = document.getElementById('tabs');
const sectionsEl = document.getElementById('sections');

CATEGORIES.forEach((cat, idx) => {
  // Tab
  const tab = document.createElement('button');
  tab.className = 'tab' + (idx === 0 ? ' active' : '');
  tab.textContent = cat.label;
  tab.dataset.idx = idx;
  tab.addEventListener('click', () => switchTab(idx));
  tabsEl.appendChild(tab);

  // Section
  const section = document.createElement('div');
  section.className = 'section' + (idx === 0 ? ' active' : '');
  section.id = 'section-' + idx;

  const perPage = 5;
  const total = cat.courses.length;
  const maxPage = Math.max(0, Math.ceil(total / perPage) - 1);

  section.innerHTML = `
    <div class="section-header">
      <div>
        <div class="section-title">${cat.label}</div>
        <div class="section-count">총 ${cat.count}개 강의</div>
      </div>
      <div class="nav-btns">
        <button class="nav-btn prev-btn" data-sec="${idx}" disabled>←</button>
        <button class="nav-btn next-btn" data-sec="${idx}" ${total <= perPage ? 'disabled' : ''}>→</button>
      </div>
    </div>
    <div class="carousel-outer">
      <div class="carousel-track" id="track-${idx}">
        ${cat.courses.map(c => makeCard(c)).join('')}
      </div>
    </div>
  `;
  sectionsEl.appendChild(section);

  // Nav logic
  section.querySelector('.prev-btn').addEventListener('click', () => move(idx, -1));
  section.querySelector('.next-btn').addEventListener('click', () => move(idx, +1));
});

const pageState = CATEGORIES.map(() => 0);

function move(secIdx, dir) {
  const cat = CATEGORIES[secIdx];
  const perPage = 5;
  const total = cat.courses.length;
  const maxPage = Math.max(0, Math.ceil(total / perPage) - 1);
  pageState[secIdx] = Math.max(0, Math.min(maxPage, pageState[secIdx] + dir));
  const track = document.getElementById('track-' + secIdx);
  const cardW = track.children[0].offsetWidth + 14;
  track.style.transform = `translateX(-${pageState[secIdx] * perPage * cardW}px)`;
  const section = document.getElementById('section-' + secIdx);
  section.querySelector('.prev-btn').disabled = pageState[secIdx] === 0;
  section.querySelector('.next-btn').disabled = pageState[secIdx] >= maxPage;
}

function switchTab(idx) {
  document.querySelectorAll('.tab').forEach((t, i) => t.classList.toggle('active', i === idx));
  document.querySelectorAll('#sections .section').forEach((s, i) => s.classList.toggle('active', i === idx));
}

// ─── SEARCH ───
const searchInput = document.getElementById('searchInput');
const searchClear = document.getElementById('searchClear');
const searchResultsEl = document.getElementById('searchResults');
const tabsWrapperEl = document.getElementById('tabsWrapper');
const sectionsEl2 = document.getElementById('sections');

function normalize(s) {
  return (s || '').toString().toLowerCase();
}

function runSearch(query) {
  const q = normalize(query).trim();
  searchClear.style.display = q ? 'block' : 'none';

  if (!q) {
    searchResultsEl.style.display = 'none';
    tabsWrapperEl.style.display = '';
    sectionsEl2.style.display = '';
    return;
  }

  tabsWrapperEl.style.display = 'none';
  sectionsEl2.style.display = 'none';
  searchResultsEl.style.display = 'block';

  const matches = [];
  CATEGORIES.forEach(cat => {
    cat.courses.forEach(c => {
      const haystack = normalize(c.title) + ' ' + normalize(c.sub) + ' ' + normalize(c.tools) + ' ' + normalize(cat.label);
      if (haystack.includes(q)) matches.push(c);
    });
  });

  if (matches.length === 0) {
    searchResultsEl.innerHTML = `<div class="search-empty">'${escapeXml(query)}'에 대한 검색 결과가 없습니다.</div>`;
    return;
  }

  searchResultsEl.innerHTML = `
    <div class="section-header">
      <div class="section-title">검색 결과 · ${matches.length}개</div>
    </div>
    <div class="search-results-grid">
      ${matches.map(c => makeCard(c)).join('')}
    </div>
  `;
}

searchInput.addEventListener('input', (e) => runSearch(e.target.value));
searchClear.addEventListener('click', () => {
  searchInput.value = '';
  runSearch('');
  searchInput.focus();
});
</script>
</body>
</html>
