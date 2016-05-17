# Lesson 2 - 會員系統 & 靜態資源管理

## 會員系統

### 一個會員系統，該要有那些功能？
1. 登入
* .....?
* .....?
* .....?

### 為什麼要用 Devise ?

因為：
1. DRY
2. 他把該做的都做好了，包含安全性以及絕大部分會員系統會需要的功能
3. 甚至把接口也做好，提供了相當的客製化空間

### 除了登入及安全性。Devise 還幫你做了什麼？
> * Database Authenticatable: hashes and stores a password in the database to validate the authenticity of a user while signing in. The authentication can be done both through POST requests or HTTP Basic Authentication.
> * Omniauthable: adds OmniAuth (https://github.com/intridea/omniauth) support.
> * Confirmable: sends emails with confirmation instructions and verifies whether an account is already confirmed during sign in.
> * Recoverable: resets the user password and sends reset instructions.
> * Registerable: handles signing up users through a registration process, also allowing them to edit and destroy their account.
> * Rememberable: manages generating and clearing a token for remembering the user from a saved cookie.
> * Trackable: tracks sign in count, timestamps and IP address.
> * Timeoutable: expires sessions that have not been active in a specified period of time.
> * Validatable: provides validations of email and password. It's optional and can be customized, so you're able to define your own validations.
> * Lockable: locks an account after a specified number of failed sign-in attempts. Can unlock via email or after a specified time period.

<br>

## 靜態資源管理

### 傳統的網站如何管理 CSS, JS, Image?
* 常見問題1：客戶端的資源未被更新 (何解)
* 常見問題2：手動 compress 很麻煩
* 常見問題3：多個 js, css 合成一份檔案時很麻煩

由於以上問題才有後來 Middleman, Grunt, Gulp 的出現


### Rails 使用 Assets-pipeline 管理這些靜態資源
* Assets-pipeline 觀念講解：https://ihower.tw/rails4/assets-pipeline.html
* Rails 4 的 Sprockets: http://guides.ruby-china.org/asset_pipeline.html

#### 上 Production 之前請記得：
```
rake assets:precompile
```

### 常見問題
1. 既然是圖片的檔名在每次 precompile 後都不一樣，如何在 css 中 include 他？  
A: http://guides.rubyonrails.org/v4.0/asset_pipeline.html#coding-links-to-assets
2. 




