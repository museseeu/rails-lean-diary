

# daily log


## 0104

how to install ruby on rails?

### generate install

By order with install `homebrew -> gpg -> rvm`

1. homebrew

http://brew.sh/index_zh-tw.html

2. gpg

Base on rvm install

3. rvm

2.3.3 使用rvm版本控制。建立 Ruby 版本。 了解目前版本

  $ rvm list known

### 實行上的概念

慣例，形式上的遵循，沒有硬性規定的法則。

  COC - 慣例優於設定

  DRY - 不要重述一樣的程式碼


### whtat's gem ?

提供安裝各種套件的管理工具。
最新版本 5.0.1，會安裝最新的 穩定 版本

  gem install rails 

### what's  great IDE ?

sublime atom VSCODE

### Basic Project 

  rails generate scaffold User name:string email:string tel:string 


`User` 整個單元慣例

`string` 只有字串可預設省略

`generate` => g

`rails db:migrate`

`rails db:rollback`


### general cmd

整合安裝相依功能。

  bundler

尋找所在位置

  which ruby


### general keymap

刪除 字元/字串 方式

  ctrl - w 字元

  ctrl - u 整串

  ctrl - r 整串最近的模糊比對


## 0106

### rails special setting

- scaffold will auto create json
- 資料處理的專長


### 實行上的概念

命名方式 my_name 慣例

外部鍵 User_id 外部鍵

關聯層: 抽象層 has many & belongs_to

query 效能問題: n + 1 問題

  * query 的監控方法，如果錯誤將最造成很大的效能問題。 

`friends` 慣例

  for friend in friends 



### what's Rails ?

Rails 框架建立，函式庫的集合體。framework > lib


### cmd

`:` symbol 

  有名字的東西。指向但並不等於。不代表任何意義，只是一個東西。

`hash`

  book = {title: "rubybook"}
  book = {:title => "rubybook"}

`.object_id`

`*` 代表展開

`(1..10) , (1...10)`


### content

  p [1, 2, 3, 4, 5].map { |n| n * 2}

  p [*1..100].reduce(&:+)


`:+` 在這裡代表的他是一個符號

變數命名不要用太隨便的名稱。

`!` 會改變原來的結果。

- 常數是英文字母開頭。
- 上層類別如果沒有寫就是object

# object oriented programming , oop

以雞蛋糕為例 蓋下去的動作就是 new

上層類別繼承，靈長目 類別(分類帽)特性稱為類別


### general cmd

採用 rails console 會自動載入。

  rails console

離開指令區

  ctrl + d or clear

### general keymap

  ctrl + l

  cmd> clear

## 0111

### what's

Q. what's PORO ?

沒有繼承任何類別，PORO => plain old ruby object
一般類別就是繼承 object

    ```
    class BankAccount 
        def initialize(amount)
        @amount = amount
    end
    ```

Q. what's spec ?

滿足了規格透過實作，就是代表完成 rspec，再確認規格前都不應該實作。
預期完成後才能實作。

猶如，倒敘法的電影，你再看第二次就會知道主角是誰。類別的全貌。

  (x)
  def deposit(amount)
    if amount > 0
      @amount += amount
    end
  end

  (o) 簡易法
  def deposit(amount)
      @amount += amount if amont > 0
  end

Q. who write the test ?

A. test 有哪些？ 
  - minitest
  - Rspec

新進工程師，實作。老鳥寫spec，測試。類別上不會有多餘的方法。只會有符合規格。寫測試不用寫完美的語法。先會動，醜沒關係。 `User model = uses`


Q. refactor ?

A. 再不改變外在行為情況價，改變內在優化。

### content

#### factory data import

進階用法，請記得看手冊。我有一個工廠，但是我不採用預設工廠。
可以讓他指向 `User model` 還有外掛可以使用快捷鍵，透過 gruad 監聽。


### general cmd

確保所有套件的狀態。就需要 `bundler install`

  rails g rspec:install


rails model create and new diff

  create 會直接寫入資料


bundle exec 就是指向該專案版本，而不是系統版本。

會載入 rails 專案 所以 rspec 會慢是正常

  rails rspec 

  gem install rspec



## 0113

### what's

Rspec 

通常會把描述寫得清楚。

  `specify(expect(bank))` 如需要單行測試，可以採用。

  `before`

  `let` 可以取代需要應用區域變數 `@` 

減少程式碼重複的呈現。需求轉換測試。

e.g. demo https://github.com/5xRuby/rspec_env


### 實行上的概念

建立 routes 重點，挑到會有混淆的的字 i, o, 1, i 

#### CRUD spec

候選人能投票

手動建立 
  新增 rails g controller welcome index
  刪除 rails d controller welcome index

  rails g model Candidate name gemder age:integer party

也可以手動，新增 file 。利用

`get "/candidates/new", to: "candidates#new"`我準備要來新增  candidates 的方法。

`> rails routes` 檢視如果打錯字將會跑出來。

`form_for(record, options = {}, &block)`
一個model 長出來的物件 `record`

`rails db:migrate` 把描述檔變成真正的資料表。

`resources :candidates`

## 0115

### what's
### content

#### partial render

partial 區段不用底線，檔名要底線。不要有`@`變數不要有主動作法。 應該是被動拿到元件並且重複使用。

#### view

盡量不要有邏輯。例如，過年打掃只是掃到別的地方而不是掃掉。丟到 helper 去管理。

#### module

模組沒有繼承。把方法寫在view 模組就能直接使用。所以模組按照英文順序讀取。ruby 方法定義在rb 

#### CRUD spec

id 是流水編號，刪掉的號碼，號碼不會再回補。

### content

並不代表只做關聯。而是會新增更多方法

ruby 沒有屬性，只有方法。
ruby 沒有屬性，只有方法。
ruby 沒有屬性，只有方法。
ruby 沒有屬性，只有方法。
ruby 沒有屬性，只有方法。

`=` 不是 `=` 在ruby 是方法的一部份


### 實行上的概念

<%= render partial: "candidate", collection: @candidates %>

`partial:` 要用完整寫法才能使用 `collection`
`collection` 取代 each 應用 @candidates 當變數 

群組這個 `collection` 區域變數也要同名，並也採用單數當 block 變數。才能合乎慣例。

<%= render collection %>

同上效果，但是必須要有單例檔案名稱，才能使用。`慣例用法`。

update | update_attributes 同樣用法，只是語義上表示。

helper 沒有用到就把檔案刪掉，因為會全部讀取。

量化表現才能知道你產值。

find_by 會new | find


### general cmd
### general keymap





### what's
### content
### general cmd
### general keymap

## 0118

## 0120

## 0122

