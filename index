<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>黑洞 AI 文学模因评估系统演示</title>
  <style>
    /* 基础布局与黑蓝渐变背景 */
    * {
      box-sizing: border-box;
    }
    body {
      margin: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      color: #e0f7fa;
      /* 深色渐变与星空般暗纹效果 */
      background: radial-gradient(circle at 20% 0%, #062042 0%, #010B1F 40%, #00060d 80%);
      min-height: 100vh;
      overflow-x: hidden;
    }
    /* 顶部标题区域 */
    header.hero {
      position: relative;
      width: 100%;
      padding: 28px 10px 24px;
      background: linear-gradient(180deg, rgba(5,20,40,0.85), rgba(2,10,25,0.85));
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      overflow: hidden;
    }
    header.hero::before {
      content: '';
      position: absolute;
      top: -30%;
      left: -50%;
      width: 200%;
      height: 200%;
      background-image: radial-gradient(circle at center, rgba(0,150,255,0.25), transparent 60%);
      transform: rotate(25deg);
      pointer-events: none;
    }
    header.hero h1 {
      margin: 0;
      font-size: 28px;
      font-weight: 700;
      color: #6dd3ff;
      text-shadow: 0 0 8px rgba(109,211,255,0.7);
    }
    header.hero .legal {
      font-size: 12px;
      line-height: 1.4;
      color: #8bb8d1;
      max-width: 520px;
      margin-top: 6px;
    }
    header.hero img.wechat {
      width: 96px;
      height: auto;
      margin-top: 8px;
      border-radius: 10px;
      box-shadow: 0 0 14px rgba(0,255,255,0.6);
    }
    /* 搜索区域样式 */
    form.search-form {
      margin: 30px auto;
      max-width: 640px;
      display: flex;
      gap: 12px;
      padding: 0 20px;
    }
    form.search-form input[type="text"] {
      flex: 1;
      padding: 14px 18px;
      border-radius: 30px;
      border: 1px solid #1d457a;
      background-color: rgba(5,18,40,0.9);
      color: #d8f0ff;
      font-size: 16px;
      outline: none;
      transition: border-color 0.3s, box-shadow 0.3s;
    }
    form.search-form input[type="text"]:focus {
      border-color: #4faeff;
      box-shadow: 0 0 10px 2px rgba(79,174,255,0.45);
    }
    form.search-form button {
      padding: 14px 26px;
      border-radius: 30px;
      border: none;
      background: linear-gradient(135deg, #0080d6 0%, #00aef4 100%);
      color: #ffffff;
      font-weight: 600;
      font-size: 16px;
      cursor: pointer;
      transition: background 0.3s, box-shadow 0.3s;
    }
    form.search-form button:hover {
      background: linear-gradient(135deg, #0098e8 0%, #0070c8 100%);
      box-shadow: 0 0 12px 2px rgba(0,130,220,0.5);
    }
    /* 结果容器与卡片布局 */
    .results {
      width: 100%;
      max-width: 1000px;
      margin: 0 auto;
      padding: 0 20px 40px;
    }
    .summary-cards {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      gap: 20px;
      margin-top: 20px;
    }
    .summary-card {
      flex: 1 1 200px;
      background: rgba(6,24,55,0.85);
      border: 1px solid rgba(60,120,200,0.4);
      border-radius: 14px;
      padding: 18px;
      text-align: center;
      box-shadow: 0 0 20px rgba(0,110,220,0.35), inset 0 0 15px rgba(0,80,160,0.35);
      backdrop-filter: blur(4px);
    }
    .summary-card .label {
      font-size: 14px;
      color: #7fc9ff;
      margin-bottom: 10px;
    }
    .summary-card .gauge {
      width: 90px;
      height: 90px;
      margin: 0 auto;
      border-radius: 50%;
      background: conic-gradient(#55f3dd 0deg, rgba(0,40,80,0.3) 0deg);
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 12px rgba(85,243,221,0.5);
      transition: background 0.6s, box-shadow 0.6s;
    }
    .summary-card .gauge::after {
      content: '';
      position: absolute;
      top: 6px;
      left: 6px;
      right: 6px;
      bottom: 6px;
      border-radius: 50%;
      background: linear-gradient(180deg, rgba(0,0,20,0.6), rgba(0,0,30,0.4));
      backdrop-filter: blur(2px);
    }
    .summary-card .value {
      position: relative;
      font-size: 28px;
      font-weight: bold;
      color: #55f3dd;
      text-shadow: 0 0 6px rgba(85,243,221,0.8);
    }
    /* 红色预警信息 */
    .warning {
      margin: 16px auto;
      padding: 10px 18px;
      border-radius: 8px;
      background: rgba(160,0,30,0.7);
      border: 1px solid rgba(255,0,60,0.8);
      color: #ffdada;
      text-align: center;
      max-width: 92%;
      box-shadow: 0 0 12px rgba(255,50,80,0.7);
      animation: pulse 1.6s infinite;
    }
    @keyframes pulse {
      0% { box-shadow: 0 0 6px rgba(255,80,100,0.6); }
      50% { box-shadow: 0 0 22px rgba(255,80,100,1.0); }
      100% { box-shadow: 0 0 6px rgba(255,80,100,0.6); }
    }
    /* 模块网格布局 */
    .grid-container {
      display: grid;
      gap: 20px;
      margin-top: 25px;
      grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
    }
    /* 翻转卡片效果 */
    .flip-card {
      perspective: 1000px;
      cursor: pointer;
    }
    .flip-card-inner {
      position: relative;
      width: 100%;
      height: 190px;
      transition: transform 0.8s;
      transform-style: preserve-3d;
      border-radius: 14px;
      overflow: hidden;
      border: 1px solid rgba(70,150,230,0.5);
      box-shadow: 0 0 18px rgba(0,130,255,0.35), inset 0 0 14px rgba(0,70,150,0.35);
      background: linear-gradient(180deg, rgba(8,28,60,0.9), rgba(3,15,40,0.9));
    }
    .flip-card.flipped .flip-card-inner {
      transform: rotateY(180deg);
    }
    .flip-card-front, .flip-card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 14px;
    }
    .flip-card-front {
      color: #9dd7ff;
    }
    .flip-card-front .title {
      font-size: 16px;
      margin-bottom: 10px;
    }
    .flip-card-front .module-gauge {
      width: 70px;
      height: 70px;
      border-radius: 50%;
      background: conic-gradient(#55f3dd 0deg, rgba(0,40,80,0.3) 0deg);
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 12px rgba(85,243,221,0.45);
      transition: background 0.6s, box-shadow 0.6s;
    }
    .flip-card-front .module-gauge::after {
      content: '';
      position: absolute;
      top: 4px;
      left: 4px;
      right: 4px;
      bottom: 4px;
      border-radius: 50%;
      background: linear-gradient(180deg, rgba(0,0,20,0.6), rgba(0,0,30,0.4));
    }
    .flip-card-front .module-value {
      position: relative;
      font-size: 22px;
      font-weight: bold;
      color: #55f3dd;
      text-shadow: 0 0 6px rgba(85,243,221,0.8);
    }
    .flip-card-back {
      transform: rotateY(180deg);
      background: linear-gradient(180deg, rgba(12,35,80,0.95), rgba(4,18,50,0.95));
      color: #f0f8ff;
      font-size: 12px;
      overflow-y: auto;
    }
    .flip-card-back h4 {
      margin: 0 0 8px;
      font-size: 16px;
      color: #6aeed0;
    }
    .flip-card-back ul {
      list-style: none;
      padding: 0;
      margin: 0;
      width: 100%;
    }
    .flip-card-back li {
      margin-bottom: 6px;
    }
    .flip-card-back li strong {
      display: block;
      font-size: 13px;
      color: #a7d8ff;
    }
    .flip-card-back li span {
      display: block;
      font-size: 12px;
      color: #8aaaca;
    }
    /* 隐藏类 */
    .hidden {
      display: none;
    }
    @media (max-width: 480px) {
      .summary-card .gauge { width: 70px; height: 70px; }
      .summary-card .value { font-size: 22px; }
      .flip-card-inner { height: 160px; }
    }
  </style>
</head>
<body>
  <header class="hero">
    <h1>黑洞&nbsp;AI&nbsp;文学模因评估系统</h1>
    <p class="legal">本页面仅做演示使用，不具备法律效力。若获取更加详尽的文学或剧本评估报告（包含相似度分析、剧本修改建议等），请联系微信。</p>
    <!-- 嵌入微信二维码（base64） -->
    <img class="wechat" src="data:image/jpeg;base64,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' alt="微信二维码">
  </header>
  <main>
    <form id="searchForm" class="search-form">
      <input type="text" id="query" placeholder="输入文学作品名称或文本" required>
      <button type="submit">分析</button>
    </form>
    <div id="results" class="results hidden">
      <div class="summary-cards">
        <div class="summary-card">
          <span class="label">综合相似度</span>
          <div class="gauge" id="overallGauge"><span class="value">0%</span></div>
        </div>
        <div class="summary-card">
          <span class="label">原创度</span>
          <div class="gauge" id="originalGauge"><span class="value">100%</span></div>
        </div>
      </div>
      <div id="warning" class="warning hidden">⚠️ 红色预警：相似度超过&nbsp;20%</div>
      <div id="modules" class="grid-container"></div>
    </div>
  </main>
  <script>
    // 模块列表定义
    const categories = ['主题','价值观','故事核','人物','结构','风格','技巧','台词'];
    // 缓存 DOM 元素
    const modulesContainer = document.getElementById('modules');
    const resultsContainer = document.getElementById('results');
    const overallGauge = document.getElementById('overallGauge');
    const originalGauge = document.getElementById('originalGauge');
    const warningElem = document.getElementById('warning');

    /**
     * 创建仪表盘样式
     * @param {HTMLElement} gaugeElem 容器元素
     * @param {number} val 百分比数值 (0-100)
     */
    function setGauge(gaugeElem, val) {
      const deg = Math.min(100, Math.max(0, val)) * 3.6;
      const color = val > 20 ? '#ff6b6b' : '#55f3dd';
      gaugeElem.style.background = `conic-gradient(${color} ${deg}deg, rgba(0,40,80,0.3) ${deg}deg)`;
      gaugeElem.style.boxShadow = `0 0 12px ${color}66`;
      const valueElem = gaugeElem.querySelector('.value') || gaugeElem.querySelector('.module-value');
      if (valueElem) {
        valueElem.textContent = `${val}%`;
        valueElem.style.color = color;
        valueElem.style.textShadow = `0 0 6px ${color}`;
      }
    }
    /**
     * 创建模块翻转卡片
     */
    function createModuleCards() {
      categories.forEach((cat, index) => {
        const card = document.createElement('div');
        card.className = 'flip-card';
        card.innerHTML = `
          <div class="flip-card-inner">
            <div class="flip-card-front">
              <span class="title">${cat}</span>
              <div class="module-gauge" id="modGauge-${index}">
                <span class="module-value">0%</span>
              </div>
            </div>
            <div class="flip-card-back">
              <h4>相似作品</h4>
              <ul id="list-${index}"></ul>
            </div>
          </div>
        `;
        card.addEventListener('click', () => {
          card.classList.toggle('flipped');
        });
        modulesContainer.appendChild(card);
      });
    }
    /**
     * 计算 Jaccard 相似度
     * @param {string} a 用户输入
     * @param {string} b 比较文本
     * @returns {number}
     */
    function computeSimilarity(a, b) {
      const normalize = (text) => text.toLowerCase().replace(/[^\p{L}\p{N}\s]/gu, ' ').split(/\s+/).filter(Boolean);
      const tokensA = new Set(normalize(a));
      const tokensB = new Set(normalize(b));
      if (!tokensA.size || !tokensB.size) return 0;
      let intersection = 0;
      tokensA.forEach(t => { if (tokensB.has(t)) intersection++; });
      const unionSize = new Set([...tokensA, ...tokensB]).size;
      return Math.round((intersection / unionSize) * 100);
    }
    /**
     * 更新汇总与模块显示
     * @param {Array} searchResults 维基搜索结果
     * @param {number} similarity 综合相似度
     */
    function updateDisplay(searchResults, similarity) {
      const overall = Math.min(100, Math.max(0, similarity));
      const originality = Math.max(0, 100 - overall);
      setGauge(overallGauge, overall);
      setGauge(originalGauge, originality);
      if (overall > 20) {
        warningElem.classList.remove('hidden');
      } else {
        warningElem.classList.add('hidden');
      }
      categories.forEach((cat, idx) => {
        // 基于综合相似度随机浮动模块得分
        const val = Math.min(100, Math.max(0, Math.round(overall + (Math.random() * 20 - 10))));
        const gaugeElem = document.getElementById(`modGauge-${idx}`);
        setGauge(gaugeElem, val);
        const listElem = document.getElementById(`list-${idx}`);
        listElem.innerHTML = '';
        // 随机展示相似作品三条
        searchResults.slice(0, 3).forEach(item => {
          const relative = Math.min(100, Math.max(0, Math.round(val + (Math.random() * 10 - 5))));
          const li = document.createElement('li');
          li.innerHTML = `<strong>${item.title}</strong><span>相似度: ${relative}%</span>`;
          listElem.appendChild(li);
        });
      });
    }
    /**
     * 调用维基百科 API 进行分析
     */
    async function performAnalysis(query) {
      resultsContainer.classList.add('hidden');
      try {
        const searchUrl = `https://en.wikipedia.org/w/api.php?action=query&list=search&srsearch=${encodeURIComponent(query)}&format=json&utf8=&origin=*`;
        const searchRes = await fetch(searchUrl);
        const searchData = await searchRes.json();
        const searchResults = searchData.query && searchData.query.search ? searchData.query.search : [];
        if (!searchResults.length) {
          alert('未找到相关作品，请尝试其他关键词。');
          return;
        }
        const first = searchResults[0];
        const pageId = first.pageid;
        const extractUrl = `https://en.wikipedia.org/w/api.php?action=query&prop=extracts&exintro&explaintext&format=json&pageids=${pageId}&utf8=&origin=*`;
        const extractRes = await fetch(extractUrl);
        const extractData = await extractRes.json();
        const pageObj = extractData.query.pages[pageId];
        const extract = pageObj && pageObj.extract ? pageObj.extract : '';
        const sim = computeSimilarity(query, extract);
        updateDisplay(searchResults, sim);
        resultsContainer.classList.remove('hidden');
      } catch (err) {
        console.error('分析失败', err);
        alert('分析失败，请检查网络连接后再试');
      }
    }
    /**
     * 页面初始化
     */
    function init() {
      createModuleCards();
      document.getElementById('searchForm').addEventListener('submit', function (e) {
        e.preventDefault();
        const query = document.getElementById('query').value.trim();
        if (query) {
          performAnalysis(query);
        }
      });
    }
    document.addEventListener('DOMContentLoaded', init);
  </script>
</body>
</html>
