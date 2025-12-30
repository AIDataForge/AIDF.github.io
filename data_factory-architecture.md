<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  
  
  <title>数据工场模块架构说明 | AI NAS 技术博客</title>
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <meta name="description" content="1. 模块概述数据工场是AI NAS的文档处理监控模块，提供文档处理状态监控、处理队列管理、处理统计等功能。 1.1 功能定位 处理监控：实时监控文档处理状态 队列管理：查看和管理处理队列 处理统计：处理性能统计和分析 异常处理：处理失败文件的恢复  1.2 访问路径 URL：&#x2F;static&#x2F;processing_monitor.html 文件位置：static&#x2F;processing_monito">
<meta property="og:type" content="article">
<meta property="og:title" content="数据工场模块架构说明">
<meta property="og:url" content="https://1660479817.github.io/AIDF.github.io/data_factory-architecture.md">
<meta property="og:site_name" content="AI NAS 技术博客">
<meta property="og:description" content="1. 模块概述数据工场是AI NAS的文档处理监控模块，提供文档处理状态监控、处理队列管理、处理统计等功能。 1.1 功能定位 处理监控：实时监控文档处理状态 队列管理：查看和管理处理队列 处理统计：处理性能统计和分析 异常处理：处理失败文件的恢复  1.2 访问路径 URL：&#x2F;static&#x2F;processing_monitor.html 文件位置：static&#x2F;processing_monito">
<meta property="og:locale" content="zh_CN">
<meta property="article:published_time" content="2025-12-30T07:50:06.000Z">
<meta property="article:modified_time" content="2025-12-30T09:21:14.959Z">
<meta property="article:author" content="AI NAS Team">
<meta property="article:tag" content="架构">
<meta property="article:tag" content="数据工场">
<meta property="article:tag" content="模块架构">
<meta name="twitter:card" content="summary">
  
    <link rel="alternate" href="/AIDF.github.io/atom.xml" title="AI NAS 技术博客" type="application/atom+xml">
  
  
    <link rel="shortcut icon" href="/AIDF.github.io/favicon.png">
  
  
  
<link rel="stylesheet" href="/AIDF.github.io/css/style.css">

  
    
<link rel="stylesheet" href="/AIDF.github.io/fancybox/jquery.fancybox.min.css">

  
  
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/fork-awesome@1.2.0/css/fork-awesome.min.css">

<meta name="generator" content="Hexo 7.3.0"></head>

<body>
  <div id="container">
    <div id="wrap">
      <header id="header">
  <div id="banner"></div>
  <div id="header-outer" class="outer">
    <div id="header-title" class="inner">
      <h1 id="logo-wrap">
        <a href="/AIDF.github.io/" id="logo">AI NAS 技术博客</a>
      </h1>
      
        <h2 id="subtitle-wrap">
          <a href="/AIDF.github.io/" id="subtitle">AI NAS 系统技术文档与分享</a>
        </h2>
      
    </div>
    <div id="header-inner" class="inner">
      <nav id="main-nav">
        <a id="main-nav-toggle" class="nav-icon"><span class="fa fa-bars"></span></a>
        
          <a class="main-nav-link" href="/AIDF.github.io/">Home</a>
        
          <a class="main-nav-link" href="/AIDF.github.io/archives">Archives</a>
        
      </nav>
      <nav id="sub-nav">
        
        
          <a class="nav-icon" href="/AIDF.github.io/atom.xml" title="RSS 订阅"><span class="fa fa-rss"></span></a>
        
        <a class="nav-icon nav-search-btn" title="搜索"><span class="fa fa-search"></span></a>
      </nav>
      <div id="search-form-wrap">
        <form action="//google.com/search" method="get" accept-charset="UTF-8" class="search-form"><input type="search" name="q" class="search-form-input" placeholder="搜索"><button type="submit" class="search-form-submit">&#xF002;</button><input type="hidden" name="sitesearch" value="https://1660479817.github.io/AIDF.github.io"></form>
      </div>
    </div>
  </div>
</header>

      <div class="outer">
        <section id="main"><article id="post-data_factory-architecture" class="h-entry article article-type-post" itemprop="blogPost" itemscope itemtype="https://schema.org/BlogPosting">
  <div class="article-meta">
    <a href="/AIDF.github.io/data_factory-architecture.md" class="article-date">
  <time class="dt-published" datetime="2025-12-30T07:50:06.000Z" itemprop="datePublished">2025-12-30</time>
</a>
    
  <div class="article-category">
    <a class="article-category-link" href="/AIDF.github.io/categories/AI-NAS-%E6%95%B0%E6%8D%AE%E5%B7%A5%E5%9C%BA/">AI NAS - 数据工场</a>
  </div>

  </div>
  <div class="article-inner">
    
    
      <header class="article-header">
        
  
    <h1 class="p-name article-title" itemprop="headline name">
      数据工场模块架构说明
    </h1>
  

      </header>
    
    <div class="e-content article-entry" itemprop="articleBody">
      
        <h2 id="1-模块概述"><a href="#1-模块概述" class="headerlink" title="1. 模块概述"></a>1. 模块概述</h2><p>数据工场是AI NAS的文档处理监控模块，提供文档处理状态监控、处理队列管理、处理统计等功能。</p>
<h3 id="1-1-功能定位"><a href="#1-1-功能定位" class="headerlink" title="1.1 功能定位"></a>1.1 功能定位</h3><ul>
<li><strong>处理监控</strong>：实时监控文档处理状态</li>
<li><strong>队列管理</strong>：查看和管理处理队列</li>
<li><strong>处理统计</strong>：处理性能统计和分析</li>
<li><strong>异常处理</strong>：处理失败文件的恢复</li>
</ul>
<h3 id="1-2-访问路径"><a href="#1-2-访问路径" class="headerlink" title="1.2 访问路径"></a>1.2 访问路径</h3><ul>
<li><strong>URL</strong>：<code>/static/processing_monitor.html</code></li>
<li><strong>文件位置</strong>：<code>static/processing_monitor.html</code></li>
<li><strong>权限要求</strong>：正式用户（USER）或管理员（ADMIN）</li>
</ul>
<h2 id="2-模块架构"><a href="#2-模块架构" class="headerlink" title="2. 模块架构"></a>2. 模块架构</h2><figure class="highlight plaintext"><table><tr><td class="gutter"><pre><span class="line">1</span><br><span class="line">2</span><br><span class="line">3</span><br><span class="line">4</span><br><span class="line">5</span><br><span class="line">6</span><br><span class="line">7</span><br><span class="line">8</span><br><span class="line">9</span><br><span class="line">10</span><br><span class="line">11</span><br><span class="line">12</span><br><span class="line">13</span><br><span class="line">14</span><br><span class="line">15</span><br><span class="line">16</span><br><span class="line">17</span><br><span class="line">18</span><br><span class="line">19</span><br><span class="line">20</span><br><span class="line">21</span><br><span class="line">22</span><br><span class="line">23</span><br><span class="line">24</span><br><span class="line">25</span><br><span class="line">26</span><br><span class="line">27</span><br><span class="line">28</span><br><span class="line">29</span><br><span class="line">30</span><br></pre></td><td class="code"><pre><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                    前端页面层                              │</span><br><span class="line">│  - processing_monitor.html (主页面)                       │</span><br><span class="line">│  - 处理状态监控组件                                        │</span><br><span class="line">│  - 队列管理组件                                            │</span><br><span class="line">│  - 统计图表组件                                            │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br><span class="line">                            ↓</span><br><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                    API接口层                              │</span><br><span class="line">│  - GET /api/v1/processing/status (处理状态)             │</span><br><span class="line">│  - GET /api/v1/processing/queue (处理队列)              │</span><br><span class="line">│  - GET /api/v1/processing/stats (处理统计)              │</span><br><span class="line">│  - GET /api/v1/processing/monitor-snapshot (监控快照)  │</span><br><span class="line">│  - GET /api/v1/processing/status-stream (状态流)        │</span><br><span class="line">│  - GET /api/v1/processing-detail/files/&#123;id&#125; (处理详情) │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br><span class="line">                            ↓</span><br><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                   业务服务层                              │</span><br><span class="line">│  - Processing Service (处理服务)                          │</span><br><span class="line">│  - Background Service (后台服务)                         │</span><br><span class="line">│  - Doc2MD Service (文档转换服务)                         │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br><span class="line">                            ↓</span><br><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                   数据层                                  │</span><br><span class="line">│  - ai_nas: processing_logs, processing_timing          │</span><br><span class="line">│  - ai_nas: file_meta, processing_checkpoints           │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br></pre></td></tr></table></figure>

<h2 id="3-核心组件"><a href="#3-核心组件" class="headerlink" title="3. 核心组件"></a>3. 核心组件</h2><h3 id="3-1-前端组件"><a href="#3-1-前端组件" class="headerlink" title="3.1 前端组件"></a>3.1 前端组件</h3><h4 id="3-1-1-处理状态监控"><a href="#3-1-1-处理状态监控" class="headerlink" title="3.1.1 处理状态监控"></a>3.1.1 处理状态监控</h4><p><strong>功能</strong>：</p>
<ul>
<li>实时显示处理状态</li>
<li>处理进度展示</li>
<li>处理阶段可视化</li>
<li>AI工作指示器</li>
</ul>
<p><strong>处理阶段</strong>：</p>
<ol>
<li><strong>初始化</strong> (initialization)</li>
<li><strong>文件验证</strong> (file_validation)</li>
<li><strong>预处理&#x2F;分析</strong> (preprocessing&#x2F;analyzer)</li>
<li><strong>解析</strong> (parsing)</li>
<li><strong>合成</strong> (synthesis)</li>
<li><strong>完成</strong> (finalization)</li>
</ol>
<h4 id="3-1-2-队列管理"><a href="#3-1-2-队列管理" class="headerlink" title="3.1.2 队列管理"></a>3.1.2 队列管理</h4><p><strong>功能</strong>：</p>
<ul>
<li>显示排队中的文件</li>
<li>显示处理中的文件</li>
<li>队列操作（暂停、恢复、取消）</li>
</ul>
<h4 id="3-1-3-统计图表"><a href="#3-1-3-统计图表" class="headerlink" title="3.1.3 统计图表"></a>3.1.3 统计图表</h4><p><strong>功能</strong>：</p>
<ul>
<li>处理性能统计</li>
<li>处理时间分析</li>
<li>处理成功率统计</li>
<li>文件类型分布</li>
</ul>
<h3 id="3-2-后端服务"><a href="#3-2-后端服务" class="headerlink" title="3.2 后端服务"></a>3.2 后端服务</h3><h4 id="3-2-1-处理服务"><a href="#3-2-1-处理服务" class="headerlink" title="3.2.1 处理服务"></a>3.2.1 处理服务</h4><p><strong>服务</strong>：<code>app/services/processing/</code></p>
<p><strong>功能</strong>：</p>
<ul>
<li>处理状态管理</li>
<li>处理队列管理</li>
<li>处理统计收集</li>
</ul>
<h4 id="3-2-2-后台服务"><a href="#3-2-2-后台服务" class="headerlink" title="3.2.2 后台服务"></a>3.2.2 后台服务</h4><p><strong>服务</strong>：<code>app/services/background/</code></p>
<p><strong>功能</strong>：</p>
<ul>
<li>任务调度</li>
<li>异步处理</li>
<li>任务监控</li>
</ul>
<h2 id="4-数据流"><a href="#4-数据流" class="headerlink" title="4. 数据流"></a>4. 数据流</h2><h3 id="4-1-状态监控流程"><a href="#4-1-状态监控流程" class="headerlink" title="4.1 状态监控流程"></a>4.1 状态监控流程</h3><figure class="highlight plaintext"><table><tr><td class="gutter"><pre><span class="line">1</span><br><span class="line">2</span><br><span class="line">3</span><br><span class="line">4</span><br><span class="line">5</span><br><span class="line">6</span><br><span class="line">7</span><br><span class="line">8</span><br><span class="line">9</span><br><span class="line">10</span><br><span class="line">11</span><br><span class="line">12</span><br></pre></td><td class="code"><pre><span class="line">页面加载</span><br><span class="line">    ↓</span><br><span class="line">请求处理状态API</span><br><span class="line">    GET /api/v1/processing/status</span><br><span class="line">    ↓</span><br><span class="line">显示处理状态</span><br><span class="line">    ├─ 总文件数</span><br><span class="line">    ├─ 处理中文件数</span><br><span class="line">    ├─ 已完成文件数</span><br><span class="line">    └─ 失败文件数</span><br><span class="line">    ↓</span><br><span class="line">定时刷新（每5秒）</span><br></pre></td></tr></table></figure>

<h3 id="4-2-实时状态流"><a href="#4-2-实时状态流" class="headerlink" title="4.2 实时状态流"></a>4.2 实时状态流</h3><figure class="highlight plaintext"><table><tr><td class="gutter"><pre><span class="line">1</span><br><span class="line">2</span><br><span class="line">3</span><br><span class="line">4</span><br><span class="line">5</span><br><span class="line">6</span><br><span class="line">7</span><br><span class="line">8</span><br><span class="line">9</span><br></pre></td><td class="code"><pre><span class="line">建立SSE连接</span><br><span class="line">    GET /api/v1/processing/status-stream</span><br><span class="line">    ↓</span><br><span class="line">接收实时状态更新</span><br><span class="line">    ├─ 文件状态变更</span><br><span class="line">    ├─ 处理进度更新</span><br><span class="line">    └─ 队列变化</span><br><span class="line">    ↓</span><br><span class="line">更新前端显示</span><br></pre></td></tr></table></figure>

<h2 id="5-技术实现"><a href="#5-技术实现" class="headerlink" title="5. 技术实现"></a>5. 技术实现</h2><h3 id="5-1-前端技术"><a href="#5-1-前端技术" class="headerlink" title="5.1 前端技术"></a>5.1 前端技术</h3><ul>
<li><strong>HTML5</strong>：页面结构</li>
<li><strong>CSS3</strong>：样式和动画</li>
<li><strong>JavaScript (ES6+)</strong>：交互逻辑</li>
<li><strong>Chart.js</strong>：图表渲染</li>
<li><strong>Server-Sent Events</strong>：实时数据推送</li>
</ul>
<h3 id="5-2-后端技术"><a href="#5-2-后端技术" class="headerlink" title="5.2 后端技术"></a>5.2 后端技术</h3><ul>
<li><strong>FastAPI</strong>：API服务</li>
<li><strong>异步处理</strong>：处理任务异步化</li>
<li><strong>任务队列</strong>：后台任务管理</li>
<li><strong>WebSocket&#x2F;SSE</strong>：实时状态推送</li>
</ul>
<h2 id="6-性能优化"><a href="#6-性能优化" class="headerlink" title="6. 性能优化"></a>6. 性能优化</h2><h3 id="6-1-前端优化"><a href="#6-1-前端优化" class="headerlink" title="6.1 前端优化"></a>6.1 前端优化</h3><ul>
<li><strong>虚拟滚动</strong>：大量数据时使用虚拟滚动</li>
<li><strong>数据缓存</strong>：状态数据缓存</li>
<li><strong>防抖处理</strong>：刷新操作防抖</li>
</ul>
<h3 id="6-2-后端优化"><a href="#6-2-后端优化" class="headerlink" title="6.2 后端优化"></a>6.2 后端优化</h3><ul>
<li><strong>查询优化</strong>：数据库索引优化</li>
<li><strong>批量查询</strong>：批量获取处理状态</li>
<li><strong>缓存机制</strong>：统计结果缓存</li>
</ul>
<h2 id="7-总结"><a href="#7-总结" class="headerlink" title="7. 总结"></a>7. 总结</h2><p>数据工场模块提供了完整的文档处理监控功能，通过实时状态更新和详细的统计信息，为用户提供了清晰的文档处理状态视图。</p>

      
    </div>
    <footer class="article-footer">
      <a data-url="https://1660479817.github.io/AIDF.github.io/data_factory-architecture.md" data-id="cmjsf781u0007vn1w9q6f08ee" data-title="数据工场模块架构说明" class="article-share-link"><span class="fa fa-share">分享</span></a>
      
      
      
  <ul class="article-tag-list" itemprop="keywords"><li class="article-tag-list-item"><a class="article-tag-list-link" href="/AIDF.github.io/tags/%E6%95%B0%E6%8D%AE%E5%B7%A5%E5%9C%BA/" rel="tag">数据工场</a></li><li class="article-tag-list-item"><a class="article-tag-list-link" href="/AIDF.github.io/tags/%E6%9E%B6%E6%9E%84/" rel="tag">架构</a></li><li class="article-tag-list-item"><a class="article-tag-list-link" href="/AIDF.github.io/tags/%E6%A8%A1%E5%9D%97%E6%9E%B6%E6%9E%84/" rel="tag">模块架构</a></li></ul>

    </footer>
  </div>
  
    
<nav id="article-nav">
  
    <a href="/AIDF.github.io/data_factory-api.md" id="article-nav-newer" class="article-nav-link-wrap">
      <strong class="article-nav-caption">前一篇</strong>
      <div class="article-nav-title">
        
          数据工场模块API接口文档
        
      </div>
    </a>
  
  
    <a href="/AIDF.github.io/home-api.md" id="article-nav-older" class="article-nav-link-wrap">
      <strong class="article-nav-caption">后一篇</strong>
      <div class="article-nav-title">系统首页模块API接口文档</div>
    </a>
  
</nav>

  
</article>


</section>
        
          <aside id="sidebar">
  
    
  <div class="widget-wrap">
    <h3 class="widget-title">分类</h3>
    <div class="widget">
      <ul class="category-list"><li class="category-list-item"><a class="category-list-link" href="/AIDF.github.io/categories/AI-NAS/">AI NAS</a></li><li class="category-list-item"><a class="category-list-link" href="/AIDF.github.io/categories/AI-NAS-Smart-Chat/">AI NAS - Smart Chat</a></li><li class="category-list-item"><a class="category-list-link" href="/AIDF.github.io/categories/AI-NAS-%E6%95%B0%E6%8D%AE%E5%B7%A5%E5%9C%BA/">AI NAS - 数据工场</a></li><li class="category-list-item"><a class="category-list-link" href="/AIDF.github.io/categories/AI-NAS-%E6%96%87%E6%A1%A3%E4%B8%AD%E5%BF%83/">AI NAS - 文档中心</a></li><li class="category-list-item"><a class="category-list-link" href="/AIDF.github.io/categories/AI-NAS-%E7%AE%A1%E7%90%86%E4%B8%AD%E5%BF%83/">AI NAS - 管理中心</a></li><li class="category-list-item"><a class="category-list-link" href="/AIDF.github.io/categories/AI-NAS-%E7%B3%BB%E7%BB%9F%E9%A6%96%E9%A1%B5/">AI NAS - 系统首页</a></li><li class="category-list-item"><a class="category-list-link" href="/AIDF.github.io/categories/AI-NAS-%E9%A1%B9%E7%9B%AE%E4%B8%AD%E5%BF%83/">AI NAS - 项目中心</a></li></ul>
    </div>
  </div>


  
    
  <div class="widget-wrap">
    <h3 class="widget-title">标签</h3>
    <div class="widget">
      <ul class="tag-list" itemprop="keywords"><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/API/" rel="tag">API</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/Smart-Chat/" rel="tag">Smart Chat</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E6%80%BB%E8%A7%88/" rel="tag">总览</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3/" rel="tag">接口文档</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E6%95%B0%E6%8D%AE%E5%B7%A5%E5%9C%BA/" rel="tag">数据工场</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E6%96%87%E6%A1%A3%E4%B8%AD%E5%BF%83/" rel="tag">文档中心</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E6%9E%B6%E6%9E%84/" rel="tag">架构</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E6%A8%A1%E5%9D%97%E6%9E%B6%E6%9E%84/" rel="tag">模块架构</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E7%AE%A1%E7%90%86%E4%B8%AD%E5%BF%83/" rel="tag">管理中心</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/" rel="tag">系统架构</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E7%B3%BB%E7%BB%9F%E9%A6%96%E9%A1%B5/" rel="tag">系统首页</a></li><li class="tag-list-item"><a class="tag-list-link" href="/AIDF.github.io/tags/%E9%A1%B9%E7%9B%AE%E4%B8%AD%E5%BF%83/" rel="tag">项目中心</a></li></ul>
    </div>
  </div>


  
    
  <div class="widget-wrap">
    <h3 class="widget-title">标签云</h3>
    <div class="widget tagcloud">
      <a href="/AIDF.github.io/tags/API/" style="font-size: 20px;">API</a> <a href="/AIDF.github.io/tags/Smart-Chat/" style="font-size: 12.5px;">Smart Chat</a> <a href="/AIDF.github.io/tags/%E6%80%BB%E8%A7%88/" style="font-size: 10px;">总览</a> <a href="/AIDF.github.io/tags/%E6%8E%A5%E5%8F%A3%E6%96%87%E6%A1%A3/" style="font-size: 20px;">接口文档</a> <a href="/AIDF.github.io/tags/%E6%95%B0%E6%8D%AE%E5%B7%A5%E5%9C%BA/" style="font-size: 12.5px;">数据工场</a> <a href="/AIDF.github.io/tags/%E6%96%87%E6%A1%A3%E4%B8%AD%E5%BF%83/" style="font-size: 15px;">文档中心</a> <a href="/AIDF.github.io/tags/%E6%9E%B6%E6%9E%84/" style="font-size: 20px;">架构</a> <a href="/AIDF.github.io/tags/%E6%A8%A1%E5%9D%97%E6%9E%B6%E6%9E%84/" style="font-size: 17.5px;">模块架构</a> <a href="/AIDF.github.io/tags/%E7%AE%A1%E7%90%86%E4%B8%AD%E5%BF%83/" style="font-size: 12.5px;">管理中心</a> <a href="/AIDF.github.io/tags/%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84/" style="font-size: 10px;">系统架构</a> <a href="/AIDF.github.io/tags/%E7%B3%BB%E7%BB%9F%E9%A6%96%E9%A1%B5/" style="font-size: 12.5px;">系统首页</a> <a href="/AIDF.github.io/tags/%E9%A1%B9%E7%9B%AE%E4%B8%AD%E5%BF%83/" style="font-size: 12.5px;">项目中心</a>
    </div>
  </div>

  
    
  <div class="widget-wrap">
    <h3 class="widget-title">归档</h3>
    <div class="widget">
      <ul class="archive-list"><li class="archive-list-item"><a class="archive-list-link" href="/AIDF.github.io/archives/2025/12/">十二月 2025</a></li></ul>
    </div>
  </div>


  
    
  <div class="widget-wrap">
    <h3 class="widget-title">最新文章</h3>
    <div class="widget">
      <ul>
        
          <li>
            <a href="/AIDF.github.io/README.md">AI NAS - 企业级智能文档管理系统</a>
          </li>
        
          <li>
            <a href="/AIDF.github.io/api.md">API接口说明文档</a>
          </li>
        
          <li>
            <a href="/AIDF.github.io/architecture.md">AI NAS 系统架构说明</a>
          </li>
        
          <li>
            <a href="/AIDF.github.io/data_factory-api.md">数据工场模块API接口文档</a>
          </li>
        
          <li>
            <a href="/AIDF.github.io/data_factory-architecture.md">数据工场模块架构说明</a>
          </li>
        
      </ul>
    </div>
  </div>

  
</aside>
        
      </div>
      <footer id="footer">
  
  <div class="outer">
    <div id="footer-info" class="inner">
      
      &copy; 2025 AI NAS Team<br>
      Powered by <a href="https://hexo.io/" target="_blank">Hexo</a>
    </div>
  </div>
</footer>

    </div>
    <nav id="mobile-nav">
  
    <a href="/AIDF.github.io/" class="mobile-nav-link">Home</a>
  
    <a href="/AIDF.github.io/archives" class="mobile-nav-link">Archives</a>
  
</nav>
    


<script src="/AIDF.github.io/js/jquery-3.6.4.min.js"></script>



  
<script src="/AIDF.github.io/fancybox/jquery.fancybox.min.js"></script>




<script src="/AIDF.github.io/js/script.js"></script>





  </div>
</body>
</html>