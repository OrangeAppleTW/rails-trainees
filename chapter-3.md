# 資料庫存取優化

Rails 其實默默地幫你做了不少優化，舉例來說，Rails 會幫你 cache 住 DB query，當你在同一個 action 中不小心做了兩次相同的 query 時，第二筆就會從 cache 中取出來用。  
> 參考：http://guides.ruby-china.org/caching_with_rails.html#sql-%E7%BC%93%E5%AD%98

## Mini-profiler

> Gem: https://github.com/MiniProfiler/rack-mini-profiler

Mini-profiler 是一個用來檢測 DB query 的 gem，詳細用法可以參考以下連結：  
https://www.hoanghiep.org/2015/07/26/miniprofiler-performance-testing-rails-applications

對 SQL 還不是太熟悉的時候，如何恰當地關聯各個資料表是個麻煩的課題。
但還好 Rails 提供的 ORM 已經幫我們處理好了許多複雜的 Query, 甚至是 Mapping。  
舉例來說，最常見的用法恐怕就是 `includes` 了。
  
  
## Model.includes(:associates)

在開發 Rails 專案時，我們能夠非常輕鬆的使用 ORM 提供的抽象層以及在Model中的設定，輕鬆地在 View 中關聯關係資料。  
舉例來說，今天如果我們要在文章列表中顯示作者名稱的名稱，最直覺的寫法恐怕就是先在 Controller 中這樣：
```ruby
@posts = Post.all
```

然後在 View 中這樣：
```erb
<% @posts.each do |post| %>
  標題：<%= post.title %>
  <br>
  作者：<%= post.user.name %>
<% end %>
```

但是在 `作者：<%= post.user.name %>` 這裡就會發生所謂的 ***N+1問題*** 了

> ### N+1 問題
> 首先 query 出 N 筆資料 (1次)，接著又用迴圈遍尋這 N 筆資料，一一送出 request (N次)，總共送出 N+1 個 request，造成效能問題。

這種問題最常出現在使用 ORM 的時候，因為用得太自然了，很容易就不小心忘記其實背後都是對資料庫做操作。  

解決方法是在使用 controller 撈出 posts 時使用 includes 方法預先將關聯的資料一起拉出來。
```ruby
@posts = Post.includes(:user)
```
這時 Rails 會使用 SQL 的 in 搜尋，預先幫你把所有符合條件的 user ***一次*** 拉出來，並且與 post 做 mapping，所以總共只有兩次的資料庫讀取。  
非常推薦看一下這篇文章，其中 N+1 問題部分也講得很清楚： https://ihower.tw/rails4/performance.html

## Counter Cache
請參考本文：http://cat-son.blogspot.tw/2013/09/rails-counter-cache.html

