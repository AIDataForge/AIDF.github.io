<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  
  
  <title>管理中心模块架构说明 | AI NAS 技术博客</title>
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <meta name="description" content="1. 模块概述管理中心是AI NAS的系统管理模块，提供用户管理、权限管理、系统设置、系统监控等功能。 1.1 功能定位 用户管理：用户创建、编辑、删除、审核 权限管理：权限分配和管理 系统设置：系统配置管理 系统监控：系统健康检查和监控 数据仓库：数据统计和分析  1.2 访问路径 用户管理：&#x2F;static&#x2F;user_management.html 系统设置：&#x2F;static&#x2F;settings.h">
<meta property="og:type" content="article">
<meta property="og:title" content="管理中心模块架构说明">
<meta property="og:url" content="https://1660479817.github.io/AIDF.github.io/management-architecture.md">
<meta property="og:site_name" content="AI NAS 技术博客">
<meta property="og:description" content="1. 模块概述管理中心是AI NAS的系统管理模块，提供用户管理、权限管理、系统设置、系统监控等功能。 1.1 功能定位 用户管理：用户创建、编辑、删除、审核 权限管理：权限分配和管理 系统设置：系统配置管理 系统监控：系统健康检查和监控 数据仓库：数据统计和分析  1.2 访问路径 用户管理：&#x2F;static&#x2F;user_management.html 系统设置：&#x2F;static&#x2F;settings.h">
<meta property="og:locale" content="zh_CN">
<meta property="article:published_time" content="2025-12-30T07:50:06.000Z">
<meta property="article:modified_time" content="2025-12-30T09:21:14.959Z">
<meta property="article:author" content="AI NAS Team">
<meta property="article:tag" content="架构">
<meta property="article:tag" content="模块架构">
<meta property="article:tag" content="管理中心">
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
        <section id="main"><article id="post-management-architecture" class="h-entry article article-type-post" itemprop="blogPost" itemscope itemtype="https://schema.org/BlogPosting">
  <div class="article-meta">
    <a href="/AIDF.github.io/management-architecture.md" class="article-date">
  <time class="dt-published" datetime="2025-12-30T07:50:06.000Z" itemprop="datePublished">2025-12-30</time>
</a>
    
  <div class="article-category">
    <a class="article-category-link" href="/AIDF.github.io/categories/AI-NAS-%E7%AE%A1%E7%90%86%E4%B8%AD%E5%BF%83/">AI NAS - 管理中心</a>
  </div>

  </div>
  <div class="article-inner">
    
    
      <header class="article-header">
        
  
    <h1 class="p-name article-title" itemprop="headline name">
      管理中心模块架构说明
    </h1>
  

      </header>
    
    <div class="e-content article-entry" itemprop="articleBody">
      
        <h2 id="1-模块概述"><a href="#1-模块概述" class="headerlink" title="1. 模块概述"></a>1. 模块概述</h2><p>管理中心是AI NAS的系统管理模块，提供用户管理、权限管理、系统设置、系统监控等功能。</p>
<h3 id="1-1-功能定位"><a href="#1-1-功能定位" class="headerlink" title="1.1 功能定位"></a>1.1 功能定位</h3><ul>
<li><strong>用户管理</strong>：用户创建、编辑、删除、审核</li>
<li><strong>权限管理</strong>：权限分配和管理</li>
<li><strong>系统设置</strong>：系统配置管理</li>
<li><strong>系统监控</strong>：系统健康检查和监控</li>
<li><strong>数据仓库</strong>：数据统计和分析</li>
</ul>
<h3 id="1-2-访问路径"><a href="#1-2-访问路径" class="headerlink" title="1.2 访问路径"></a>1.2 访问路径</h3><ul>
<li><strong>用户管理</strong>：<code>/static/user_management.html</code></li>
<li><strong>系统设置</strong>：<code>/static/settings.html</code></li>
<li><strong>Agent配置</strong>：<code>/static/settings.html?tab=agent-config</code></li>
<li><strong>系统监控</strong>：<code>/static/system_health.html</code></li>
<li><strong>数据仓库</strong>：<code>/static/stats_dashboard.html</code></li>
<li><strong>权限要求</strong>：管理员（ADMIN）</li>
</ul>
<h2 id="2-模块架构"><a href="#2-模块架构" class="headerlink" title="2. 模块架构"></a>2. 模块架构</h2><figure class="highlight plaintext"><table><tr><td class="gutter"><pre><span class="line">1</span><br><span class="line">2</span><br><span class="line">3</span><br><span class="line">4</span><br><span class="line">5</span><br><span class="line">6</span><br><span class="line">7</span><br><span class="line">8</span><br><span class="line">9</span><br><span class="line">10</span><br><span class="line">11</span><br><span class="line">12</span><br><span class="line">13</span><br><span class="line">14</span><br><span class="line">15</span><br><span class="line">16</span><br><span class="line">17</span><br><span class="line">18</span><br><span class="line">19</span><br><span class="line">20</span><br><span class="line">21</span><br><span class="line">22</span><br><span class="line">23</span><br><span class="line">24</span><br><span class="line">25</span><br><span class="line">26</span><br><span class="line">27</span><br><span class="line">28</span><br><span class="line">29</span><br><span class="line">30</span><br><span class="line">31</span><br><span class="line">32</span><br><span class="line">33</span><br></pre></td><td class="code"><pre><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                    前端页面层                              │</span><br><span class="line">│  - user_management.html (用户管理)                       │</span><br><span class="line">│  - settings.html (系统设置)                              │</span><br><span class="line">│  - system_health.html (系统监控)                         │</span><br><span class="line">│  - stats_dashboard.html (数据仓库)                       │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br><span class="line">                            ↓</span><br><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                    API接口层                              │</span><br><span class="line">│  - GET /api/v1/user-management/users (用户列表)         │</span><br><span class="line">│  - POST /api/v1/user-management/users (创建用户)        │</span><br><span class="line">│  - GET /api/v1/permission-management/permissions (权限) │</span><br><span class="line">│  - GET /api/v1/system/info (系统信息)                   │</span><br><span class="line">│  - GET /api/v1/health/check (健康检查)                  │</span><br><span class="line">│  - GET /api/v1/stats/dashboard (统计数据)               │</span><br><span class="line">│  - GET /api/v1/agent-config/modules (Agent配置)        │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br><span class="line">                            ↓</span><br><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                   业务服务层                              │</span><br><span class="line">│  - Auth Service (认证服务)                               │</span><br><span class="line">│  - User Management Service (用户管理服务)                │</span><br><span class="line">│  - Permission Service (权限服务)                         │</span><br><span class="line">│  - System Service (系统服务)                             │</span><br><span class="line">│  - Health Service (健康检查服务)                         │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br><span class="line">                            ↓</span><br><span class="line">┌─────────────────────────────────────────────────────────┐</span><br><span class="line">│                   数据层                                  │</span><br><span class="line">│  - ai_nas_app: users, roles, permissions               │</span><br><span class="line">│  - ai_nas: system_logs, processing_logs                 │</span><br><span class="line">└─────────────────────────────────────────────────────────┘</span><br></pre></td></tr></table></figure>

<h2 id="3-核心组件"><a href="#3-核心组件" class="headerlink" title="3. 核心组件"></a>3. 核心组件</h2><h3 id="3-1-用户管理"><a href="#3-1-用户管理" class="headerlink" title="3.1 用户管理"></a>3.1 用户管理</h3><p><strong>功能</strong>：</p>
<ul>
<li>用户列表展示</li>
<li>用户创建和编辑</li>
<li>用户审核（批准&#x2F;拒绝）</li>
<li>密码重置</li>
<li>用户统计</li>
</ul>
<h3 id="3-2-权限管理"><a href="#3-2-权限管理" class="headerlink" title="3.2 权限管理"></a>3.2 权限管理</h3><p><strong>功能</strong>：</p>
<ul>
<li>权限列表管理</li>
<li>用户权限分配</li>
<li>角色权限配置</li>
<li>权限统计</li>
</ul>
<h3 id="3-3-系统设置"><a href="#3-3-系统设置" class="headerlink" title="3.3 系统设置"></a>3.3 系统设置</h3><p><strong>功能</strong>：</p>
<ul>
<li>系统配置管理</li>
<li>LLM配置</li>
<li>VLM配置</li>
<li>Embedding配置</li>
<li>Agent配置</li>
</ul>
<h3 id="3-4-系统监控"><a href="#3-4-系统监控" class="headerlink" title="3.4 系统监控"></a>3.4 系统监控</h3><p><strong>功能</strong>：</p>
<ul>
<li>系统健康检查</li>
<li>性能监控</li>
<li>错误日志查看</li>
<li>系统状态展示</li>
</ul>
<h3 id="3-5-数据仓库"><a href="#3-5-数据仓库" class="headerlink" title="3.5 数据仓库"></a>3.5 数据仓库</h3><p><strong>功能</strong>：</p>
<ul>
<li>文档统计</li>
<li>趋势分析</li>
<li>词云可视化</li>
<li>数据导出</li>
</ul>
<h2 id="4-总结"><a href="#4-总结" class="headerlink" title="4. 总结"></a>4. 总结</h2><p>管理中心模块提供了完整的系统管理功能，通过统一的API接口和清晰的功能划分，为管理员提供了便捷的系统管理工具。</p>

      
    </div>
    <footer class="article-footer">
      <a data-url="https://1660479817.github.io/AIDF.github.io/management-architecture.md" data-id="cmjsez65l000hy71w4uvlgxyu" data-title="管理中心模块架构说明" class="article-share-link"><span class="fa fa-share">分享</span></a>
      
      
      
  <ul class="article-tag-list" itemprop="keywords"><li class="article-tag-list-item"><a class="article-tag-list-link" href="/AIDF.github.io/tags/%E6%9E%B6%E6%9E%84/" rel="tag">架构</a></li><li class="article-tag-list-item"><a class="article-tag-list-link" href="/AIDF.github.io/tags/%E6%A8%A1%E5%9D%97%E6%9E%B6%E6%9E%84/" rel="tag">模块架构</a></li><li class="article-tag-list-item"><a class="article-tag-list-link" href="/AIDF.github.io/tags/%E7%AE%A1%E7%90%86%E4%B8%AD%E5%BF%83/" rel="tag">管理中心</a></li></ul>

    </footer>
  </div>
  
    
<nav id="article-nav">
  
    <a href="/AIDF.github.io/management-api.md" id="article-nav-newer" class="article-nav-link-wrap">
      <strong class="article-nav-caption">前一篇</strong>
      <div class="article-nav-title">
        
          管理中心模块API接口文档
        
      </div>
    </a>
  
  
    <a href="/AIDF.github.io/project_center-api.md" id="article-nav-older" class="article-nav-link-wrap">
      <strong class="article-nav-caption">后一篇</strong>
      <div class="article-nav-title">项目中心模块API接口文档</div>
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