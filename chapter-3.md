# 資料庫存取優化

## Mini-profiler

> Gem: https://github.com/MiniProfiler/rack-mini-profiler

Mini-profiler 是一個用來檢測 DB query 的 gem，詳細用法可以參考以下連結：  
https://www.hoanghiep.org/2015/07/26/miniprofiler-performance-testing-rails-applications

對 SQL 還不是太熟悉的時候，如何恰當地關聯各個資料表是個麻煩的課題。
但還好 Rails 提供的 ORM 已經幫我們處理好了許多複雜的 Query, 甚至是 Mapping。  
舉例來說，最常見的用法恐怕就是 `includes` 了。
  
  
## Model.includes(:associates)

在開發 Rails 專案時，我們能夠非常輕鬆的使用 ORM 提供的抽象層以及在Model中的設定，輕鬆地在 View 中關聯關係資料，舉例來說：

### Case 1 - 在文章列表中顯示作者名稱
今天如果我們要在文章列表中顯示作者名稱的名稱，最直覺的寫法恐怕就是先在 Controller 中這樣：
```
@posts = Post.all
```

然後在 View 中這樣：
```
<% @posts.each do |post| %>
  標題：<%= post.title %>
  <br>
  作者：<%= post.user.name %>
<% end %>
```

但是在 `作者：<%= post.user.name %>` 這裡就會發生所謂的 ***N+1問題*** 了

> ### N+1 問題
> 
