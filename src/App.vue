<template>
  <div>
    <h3>Search Multiple Sites</h3>
    <div v-for="site in sites" :key="site.name">
      <input type="checkbox" v-model="selectedSites" :value="site" />
      <label>{{ site.name }}</label>
    </div>
    <input v-model="searchQuery" placeholder="Enter search term" />
    <button @click="search">Fire!</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      searchQuery: '',
      selectedSites: [],
      sites: [
        { name: 'Google', url: 'https://www.google.com/search?q=' },
        { name: 'Bing', url: 'https://www.bing.com/search?q=' },
        { name: '百度', url: 'https://www.baidu.com/s?wd=' },
        { name: 'DuckDuckGo', url: 'https://duckduckgo.com/?q=' },
        { name: 'Yahoo Japan', url: 'https://search.yahoo.co.jp/search?p=' },
        { name: 'Youtube', url: 'https://www.youtube.com/results?search_query=' },
        { name: 'Emacs 中文', url: 'https://emacs-china.org/search?q=' },
        { name: '豆瓣音乐', url: 'https://search.douban.com/music/subject_search?search_text=' },
        { name: '豆瓣读书', url: 'https://search.douban.com/book/subject_search?search_text=' },
        { name: '豆瓣电影', url: 'https://search.douban.com/movie/subject_search?search_text=' },
        { name: 'Hackernews', url: 'https://hn.algolia.com/?query=' },
        {
          name: 'Desuarchive', url: 'https://desuarchive.org/g/search/text/',
          description: '[a/aco/an/c/cgl/co/d/fit/g/his/int/k/m/mlp/mu/q/qa/r9k/tg/trash/vr/wsg]'
        },
        { name: 'Stack Exchange', url: 'https://stackexchange.com/search?q=' },
        { name: '维基百科', url: 'https://zh.wikipedia.org/w/index.php?search=' },
        { name: 'Wikipedia', url: 'https://en.wikipedia.org/w/index.php?search=' },
        { name: 'ウィキペディア', url: 'https://ja.wikipedia.org/w/index.php?search=' },
        { name: '위키백과', url: 'https://ko.wikipedia.org/w/index.php?search=' },
        { name: 'Naver', url: 'https://search.naver.com/search.naver?query=' },
        { name: 'Yandex', url: 'https://yandex.com/search/?text=' },
        { name: 'SRFI', url: 'https://srfi.schemers.org/?q=' },
        { name: 'Pitchfork', url: 'https://pitchfork.com/search/?q=' },
        { name: '网易云音乐（登录）', url: 'https://music.163.com/#/search/m/?s=' },
        { name: 'Last.fm', url: 'https://www.last.fm/search?q=' },
        { name: 'InternetArchive', url: 'https://web.archive.org/web/20240000000000*/WIndows%2011' },
        { name: 'Bilibili', url: 'https://search.bilibili.com/all?keyword=' },
        { name: 'Z-Library', url: 'https://singlelogin.re/s/?q=' },
        { name: 'Rutracker（登录）', url: 'https://rutracker.org/forum/tracker.php?nm=' },
        { name: 'MDN Docs', url: 'https://developer.mozilla.org/en-US/search?q=' },
        { name: 'Google Scholar', url: 'https://scholar.google.com/scholar?q=' },
        { name: '中国知网', url: 'https://kns.cnki.net/kns8s/defaultresult/index?kw=' },
        { name: 'dblp', url: 'https://dblp.org/search?q=' },
        { name: 'Connected papers', url: 'https://www.connectedpapers.com/search?q=' },
        { name: '知乎（登录）', url: 'https://www.zhihu.com/search?q=' },
        { name: 'Github', url: 'https://github.com/search?q=' },
        { name: '小红书（登录）', url: 'https://www.xiaohongshu.com/search_result?keyword=' },
        { name: 'Quora（登录）', url: 'https://www.quora.com/search?q=' },
        { name: 'X/Twitter', url: 'https://x.com/search?q=' },
        { name: 'TikTok', url: 'https://www.tiktok.com/search?q=' },
        { name: 'GreasyFork', url: 'https://greasyfork.org/en/scripts?q=' },
        {
          name: 'Devdocs', url: 'https://devdocs.io/', callback: (url, searchQuery) => {
            const newpage = window.open(`${url}`)
            newpage.focus()
            console.log(newpage)
            document.head.innerHTML = '<title>Hi</title></head>';
            document.body.innerHTML = '<body>' + html + '</body>';
            var script = document.createElement('script');
            script.src = 'js/myScript.js';
            document.head.appendChild(script);
          }},
      ]
  };
},
methods: {
  search() {
    this.selectedSites.forEach(site => {
      console.log(site)
      if ('callback' in site) {
        site.callback(site.url, this.searchQuery)
      } else {
        window.open(`${site.url}${encodeURIComponent(this.searchQuery)}`, '_blank');
      }
    });
  },

  insert() {
    document.head.innerHTML = '<title>Hi</title></head>';
    
    document.body.style.border = "5px solid red";

  }
}
};
</script>
