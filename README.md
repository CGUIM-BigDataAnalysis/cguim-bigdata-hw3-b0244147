長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest) 
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
PttMovie<-"https://www.ptt.cc/bbs/movie/index.html"
for(n in 1:6){
  PttContent <- read_html(PttMovie)
  pageup <- PttContent %>% html_nodes(".btn-group a") %>% html_attr("href")
  post_title <- PttContent %>% html_nodes(".title") %>% html_text()
  post_push <- PttContent %>% html_nodes(".nrec") %>% html_text()
  post_author <- PttContent %>% html_nodes(".author") %>% html_text()
  PttMovie_posts <- data.frame(Title = post_title,
                               PushNum = post_push,
                               Author = post_author)
  PttMovie <- paste("https://www.ptt.cc",pageup[4], sep="")
  nam <- paste("PttMovie_posts",n,sep="")
  assign(nam, PttMovie_posts)
}
PttMovie_posts_All <- rbind(PttMovie_posts1,PttMovie_posts2,PttMovie_posts3,PttMovie_posts4,PttMovie_posts5,PttMovie_posts6)
```

爬蟲結果呈現
------------

``` r
knitr::kable(PttMovie_posts_All[c("Title", "PushNum", "Author")]) 
```

| Title                                                           | PushNum | Author       |
|:----------------------------------------------------------------|:--------|:-------------|
| \[好雷\] 《愛在午夜希臘時》超紓壓又享受！                       |         | Mood10207    |
| \[極好雷\]美女與野獸--完美重現經典~感動更勝                     |         | cowayneish   |
| \[公告\]《各式疑難雜症FAQ》                                     | 23      | yunyun85106  |
| \[公告\] 板規！必看！｜好文推薦‧惡文檢舉                        | 爆      | ericf129     |
| \[好雷\]最愛你的人是我：藏在濫性與畸戀中的純真                  | 1       | z0etic       |
| \[新聞\] 金剛戰士　影史首部涉及同性戀元素超級英                 | 19      | Naple        |
| Fw: \[新聞\] 「X教授」獲頒傳奇獎　當眾與老友「磁力              | 27      | southring    |
| \[討論\] 小勞勃道尼將演"怪醫杜立德"                             | 37      | jay5566      |
| \[好雷\] 《長假漫漫》(Permanent Vacation)                       | 1       | leila        |
| \[討論\]《不可能的任務6》將打造前所未見的動作！                 | 43      | jay5566      |
| \[雷\] 《乘風破浪》韓寒的幽默與懷舊青年夢                       | 1       | ghooh        |
| \[情報\] 免費看friDay影音x39th金穗獎線上影展                    |         | pttkitty     |
| \[討論\] 張藝謀三國新片卡司曝光！！！！！                       | 34      | jay5566      |
| \[無雷\] 大推救殭清道夫                                         |         | ULTIMA1002   |
| \[好雷\] 救殭清道夫 我的殭屍女友                                |         | uhbygv45     |
| \[贈票\] 電影《我的叔叔》 特映券                                |         | rascaltseng  |
| \[負雷\] 看得好累的金剛                                         |         | benjamin0830 |
| \[贈票\] 威秀Mappa主題電影饗宴「非普通型男」                    |         | youguysuck   |
| Re: \[請益\] Ancient One, Chosen One 怎麼翻比較好?              | 5       | S890127      |
| \[贈票\] 星際異攻隊2 電影票兩張                                 |         | ck980417     |
| \[問片\] 一部韓國電影                                           | 5       | sofar14      |
| \[好雷\] 真假模糊的七月與安生                                   | 1       | aiya0824     |
| \[新聞\] 史嘉蕾喬涵森主演《攻殼機動隊》釋出「                   | 4       | zoicu        |
| \[片單\] 曾經讓你崩潰大哭的電影                                 | 爆      | timblue0823  |
| \[普雷\] 白蟻                                                   | 3       | a031405      |
| \[情報\] 溫斯坦再戰奧斯卡！魯妮、BC等主演三部新電影排定上映檔期 | 13      | qpr322       |
| \[神雷\] 寫給過去回憶的「情書」                                 | 4       | Changyaya    |
| \[好雷\] 明天，我要和昨天的妳約會                               | 12      | imhermit     |
| \[選片\] 異星智慧vs金剛戰士vs聲之形vs金爆內幕                   | 29      | Emerson158   |
| \[討論\] HISHE該怎麼完結 俠盜一號/20個實體特效                  | 5       | dendenomg    |
| (本文已被刪除) \[yp20020220\]                                   |         | -            |
| \[請益\]攻殼機動隊                                              | 4       | dickygto     |
| \[新聞\] 徐靜蕾談《綁架者》：這部電影才是我，簡                 | 2       | arielhsiao   |
| \[請益\] Ancient One, Chosen One 怎麼翻比較好?                  | 49      | PrinceBamboo |
| \[微好雷\]寂林殺機(無聲夜)-就兩個人不無聊嗎?                    |         | LittleDiDi   |
| \[問片\] 從美術館偷畫的結局                                     | 10      | benson820827 |
| \[好雷\] 當他們認真編織時—成為一個好媽媽                        | 2       | duoCindy     |
| \[討論\] 片頭一開始就很恐怖的電影                               | 43      | rkb3432      |
| \[新聞\] 「包租婆」改吃棒棒糖？景甜新髮型登場                   | 7       | Naple        |
| \[新聞\] 美女與野獸 破英國三月電影開畫紀錄                      | 9       | AnneofGreen  |
| \[討論\] 這個陣容有沒有搞頭？                                   |         | KOYOYO       |
| Re: \[贈票\] 【攻殼機動隊】台北IMAX 3D特映會搶先看              | 15      | ChloeD       |
| \[好雷\] 救殭清道夫 沒女友的快去挖墳                            | 1       | siglar       |
| \[討論\] 美女與野獸很衰的王子                                   | 4       | zhahu        |
| \[好雷\] 華人奇幻電影的新境界--封神傳奇                         | 21      | senria       |
| \[好雷\] 動畫版/2014法版/2017真人版《美女與野獸》 綜合比較心得  | 8       | amandawang   |
| \[問片\] (已解決)某一部以宇宙中航行的船艦為背景                 |         | bryanma      |
| \[問片\] 兩部有點年代的動畫電影                                 | 10      | HighGot      |
| \[討論\] 《金牌特務２》將提前一週至九月底上映？                 | 22      | SKnight      |
| \[新聞\] 《美女與野獸》艾瑪華森酬勞預計拿4.6億                  | 45      | jay5566      |
| Re: \[問片\] 找一部夫妻被綁，妻子卻與綁匪%%%                    | 2       | PegasusSeiya |
| \[討論\]漢斯季默:我看不見班飾演蝙蝠俠內心痛苦！                 | 爆      | jay5566      |
| (本文已被刪除) \[feelingtree\]                                  |         | -            |
| \[新聞\] 【電影版聲之形】獲文化廳媒體藝術祭肯定                 | 4       | kkaicd1      |
| \[選片\] 美女與野獸二刷要看3D還是IMAX                           | 12      | b08297       |
| \[問片\] 10~15年以前的外國喜劇校園電影                          | 4       | shanyaochung |
| \[片單\] 難以抉擇的價值觀                                       | 9       | feelingtree  |
| \[問片\] 一部男主被訓練成殺手的片                               | 11      | ejijo761115  |
| \[情報\] 史嘉蕾喬韓森《女狼嗨到趴》前導預告                     | 28      | SKnight      |
| \[討論\] 迪士尼公主偏愛藍裙？色彩專家解釋原因                   | 19      | vupmp6       |
| \[片單\] 太空艙 有三個太空人漂浮場景                            | 22      | Nexus5X      |
| \[普雷\] 比想像中好的美女與野獸                                 | 20      | ronale       |
| \[超好雷\] 厭世是因為太喜歡世界：《最後的詩句》                 | 21      | Fantasyweed  |
| \[問片\] 異國戀情老電影                                         | 1       | tenbad       |
| \[新聞\] 《長城》太驚人　景甜二度登基爛片女帝                   | 24      | vm04vm04     |
| \[討論\] 最愛安海瑟威演的哪部片                                 | 78      | litann4      |
| Re: \[討論\] Emma Watson是不是只能演小女生？                    | 9       | denverkober  |
| \[贈票\]【攻殼機動隊】IMAX 3D 14分鐘特別片段                    | 爆      | ChloeD       |
| \[討論\] 金剛:骷髏島，女主角的相機                              | 7       | kiwistar     |
| \[問片\] 很久很久的電影不知道片名                               | 6       | fish60233    |
| \[新聞\] 曾經轟動全台！「魔鬼終結者2」3D版今秋                  | 29      | fff15973     |
| \[好雷\] 絕鯊島The Shallows                                     | 15      | ueiwei       |
| \[贈票\] 橫掃義大利金獎大導《媽媽教我愛的一切》                 | 72      | indiasosp    |
| \[討論\] 祝多藍生日快樂，這個多藍好日系                         | 4       | r123tw       |
| \[新聞\] 景甜俏麗套GUCCI　黏邪神洩綜藝魂                        | 28      | shinbird     |
| \[好雷\] 美女與野獸<sub>我看的是童年不是童話</sub>              | 31      | tsukachan    |
| \[普雷\]《乘風破浪》- 韓寒呼叫1998                              | 1       | jk10134      |
| \[微好雷\] 當他們認真編織時                                     | 3       | u850234      |
| \[好雷\] 奔奔奔 Burn Burn Burn，唐頓二姐壓馬路                  | 2       | mysmalllamb  |
| Re: \[LIVE\] 刺激1995 AXN 21:00                                 | 3       | Sturmvogel   |
| \[問片\] 找一部夫妻被綁，妻子卻與綁匪%%%                        | 17      | ejijo761115  |
| \[好雷\] 真人版《美女與野獸》最喜歡的改編？                     | 15      | freiheitkino |
| \[情報\] 韓國電影《叛獄無間》4/7在台上映                        | 4       | LeedTV       |
| \[普雷\] 美女與野獸小吐槽                                       | 38      | sarasay      |
| \[好雷\] 美女與野獸隨筆心得                                     | 3       | MYLIUUU      |
| \[普偏好雷\]美女與野獸 比預期普通一些                           | 20      | s2657507     |
| Re: \[超爛雷\] 自殺小隊，連BvS都可以屌打這部爛片                | 9       | KingKingCold |
| \[好雷\] 美女與野獸--野獸長大了                                 | 12      | COCOCCC      |
| Re: \[請益\] 明天，我要和昨天的妳約會 時間線                    | 7       | nasuchan     |
| \[贈票\] 3/29金馬奇幻影展特映會                                 | 1       | mid729       |
| Fw: \[閒聊\] 誤闖進 Cyberpunk潮流的香港九龍城寨                 | 4       | patdolye     |
| \[新聞\] 艾莉西亞薇坎德將演出摩天樓導演新片                     | 6       | sampsonlu919 |
| Re: \[失望雷\] 羅根 確認福斯真的沒心經營X戰警系列               | 20      | tomgod17     |
| \[普好雷\] 完全沒看過X戰警下的羅根觀感                          | 16      | NCKUFatPork  |
| \[片單\] 青貧世代議題電影推薦                                   | 16      | ragnarokfans |
| \[好雷\] 《三笑》(1964)（主談秋香）                             | 8       | metz1552     |
| \[好雷\] 美女與野獸，重新認識貝兒                               | 2       | Edouard      |
| \[新聞\] 裸照門爆75人名單 泰勒絲布麗拉森驚駭                    | 10      | zkow         |
| \[新聞\] 史嘉蕾拍片集郵亞洲城市 憶《露西》讚台北                | 16      | zkow         |
| \[新聞\] 美女與野獸 首週末全球票房3.5億美元                     | 79      | lovemelissa  |
| \[討論\] 大家覺得新還舊版美女與野獸主題曲好聽？                 | 35      | Ga1axyNote7  |
| \[片單\] 關於急救創傷處理的電影                                 | 24      | angel5230    |
| \[討論\] 大家聊聊那些原創電影未來可能還會重拍                   | 20      | fightclubgf  |
| \[新聞\] 《攻殼機動隊》1995年動畫原版5月攻台                    | 6       | CatchPlay    |

解釋爬蟲結果
------------

``` r
str(PttMovie_posts_All)
```

    ## 'data.frame':    104 obs. of  3 variables:
    ##  $ Title  : Factor w/ 104 levels "\n\t\t\t\n\t\t\t\t[公告] 板規！必看！｜好文推薦‧惡文檢舉\n\t\t\t\n\t\t\t",..: 3 4 2 1 9 18 23 11 6 13 ...
    ##  $ PushNum: Factor w/ 38 levels "","23","爆","1",..: 1 1 2 3 4 5 6 8 4 10 ...
    ##  $ Author : Factor w/ 94 levels "cowayneish","ericf129",..: 3 1 4 2 21 11 16 9 10 9 ...

``` r
"爬出103個文章標題"
```

    ## [1] "爬出103個文章標題"

解釋解釋解釋解釋

``` r
table(PttMovie_posts_All$Author)
```

    ## 
    ##   cowayneish     ericf129    Mood10207  yunyun85106     aiya0824 
    ##            1            1            1            1            1 
    ## benjamin0830     ck980417        ghooh      jay5566        leila 
    ##            1            1            1            5            1 
    ##        Naple     pttkitty  rascaltseng      S890127      sofar14 
    ##            2            1            1            1            1 
    ##    southring  timblue0823     uhbygv45   ULTIMA1002   youguysuck 
    ##            1            1            1            1            1 
    ##       z0etic        zoicu            -      a031405  AnneofGreen 
    ##            1            1            2            1            1 
    ##   arielhsiao benson820827    Changyaya       ChloeD    dendenomg 
    ##            1            1            1            2            1 
    ##     dickygto     duoCindy   Emerson158     imhermit       KOYOYO 
    ##            1            1            1            1            1 
    ##   LittleDiDi PrinceBamboo       qpr322      rkb3432       siglar 
    ##            1            1            1            1            1 
    ##        zhahu   amandawang       b08297      bryanma  ejijo761115 
    ##            1            1            1            1            2 
    ##  Fantasyweed  feelingtree      HighGot      kkaicd1      Nexus5X 
    ##            1            1            1            1            1 
    ## PegasusSeiya       ronale       senria shanyaochung      SKnight 
    ##            1            1            1            1            2 
    ##       tenbad       vupmp6  denverkober     fff15973    fish60233 
    ##            1            1            1            1            1 
    ## freiheitkino    indiasosp      jk10134     kiwistar       LeedTV 
    ##            1            1            1            1            1 
    ##      litann4  mysmalllamb       r123tw      sarasay     shinbird 
    ##            1            1            1            1            1 
    ##   Sturmvogel    tsukachan      u850234       ueiwei     vm04vm04 
    ##            1            1            1            1            1 
    ##    angel5230    CatchPlay      COCOCCC      Edouard  fightclubgf 
    ##            1            1            1            1            1 
    ##  Ga1axyNote7 KingKingCold  lovemelissa     metz1552       mid729 
    ##            1            1            1            1            1 
    ##      MYLIUUU     nasuchan  NCKUFatPork     patdolye ragnarokfans 
    ##            1            1            1            1            1 
    ##     s2657507 sampsonlu919     tomgod17         zkow 
    ##            1            1            1            2

``` r
"jay5566 5times"
```

    ## [1] "jay5566 5times"

解釋解釋解釋解釋

``` r
"雖然不知道JAY5566是誰 但是他的文章推文數量都滿多的"
```

    ## [1] "雖然不知道JAY5566是誰 但是他的文章推文數量都滿多的"
