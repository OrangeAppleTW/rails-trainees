# Chapter 1 - 基礎知識
* 時間: 1hr

## Rails
### 為什麼需要用Framework?
* 容易協作，維護性佳
* 少想一些事情，開發更快
* 安全
* 接口設計良好 (Middleware)

### Rails 是什麼？
* 一個 ruby 程式，可以藉由 gem 安裝
* 安裝後，能在 terminal 啟動一個新專案： `rails new [專案名稱]`
* 之後會產生一堆 folder 和 file，可以輸入 `rails s` 來執行

### MVC 架構
* 定義有點眾說紛紜，也不用太追究，大致上是：
  * Model - 處理商業邏輯，負責資料庫的連結以及資料的行為
  * Controller - 骨幹，處理資料流，負責呼叫 model 以及 render View
  * View - 頁面，可以想像成 php，能將後段資料 echo 在 HTML 中
  
### Template Engine
* 預設採用 [erb](https://ihower.tw/rails4/actionview.html)，但是建議改用 [slim](http://slim-lang.com/) 加快撰寫速度（類似 jade）
* 

## Gems & Bundler
* 管理所使用的套件，一鍵安裝/升級
* 專案中要用到的的 Gem 都放在 Gemfile

## Ruby
要學 Rails, ruby 不用太好，但是需要知道以下知識
* Ruby 的 變數有三種：http://guides.ruby.tw/ruby/variables.html
* Ruby 沒有 `++`
* Ruby 的 `else if` 寫作 `elsif`
* 在 Ruby 中，一切都是物件 `5.times {puts "Hello world"}`
* 要試一下 ruby 的語法，可以在終端機下輸入 `irb` 叫出 ruby console

## ORM

## Database

## SQL
- miniprofiler

## DOM & jQuery


## 潮潮的前端 framework
- 組字串，然後 append
- 其實你最常用的是 template 

## AJAX
- 不要用

----

## Homework
* 用 rails 寫一個部落格，能夠發文、留言，所以至少需要 posts, comments 兩張 table
* 不用使用 slim, 用原生的 erb 即可
* 使用 scaffold 建 migration

> ### Hint:
> * Scaffold 請參考：http://railsbridge-docs-zh-tw.herokuapp.com/%E5%88%9D%E6%8E%A2-rails/%E5%BB%BA%E7%AB%8B_migration
> * scaffold 完之後請觀察： model, controller, view, migration 資料夾新增的檔案, route.rb
> * 也可以在 terminal 下執行 `rake routes` 看看目前的 routing list
