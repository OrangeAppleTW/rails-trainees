# 資料庫存取優化

## Mini-profiler

> Gem: https://github.com/MiniProfiler/rack-mini-profiler

Mini-profiler 是一個用來檢測 DB query 的 gem，詳細用法可以參考以下連結：  
https://www.hoanghiep.org/2015/07/26/miniprofiler-performance-testing-rails-applications

對 SQL 還不是太熟悉的時候，如何恰當地關聯各個資料表是個麻煩的課題。
但還好 Rails 提供的 ORM 已經幫我們處理好了許多複雜的 Query, 甚至是 Mapping。  
舉例來說，最常見的用法恐怕就是 `includes` 了。

# Model.includes(:associates)
