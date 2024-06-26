---
title: 資工所落榜心得
tags:
  - Others
toc: false
date: 2024-05-30 14:00:00
---


網路上已經有很多 XXX 跨考錄取資工所心得，所以來寫一篇落榜心得好了，希望可以稍微彌補一下倖存者偏差。

<!-- more -->

本篇文章預計分成以下幾個部份：

- 自身背景和報考動機
- 準備過程
- 心得

### 自身背景與報考動機

身為一位非本科系轉職的軟體工程師，而且還是別人眼中的前端難民，剛開始工作，需要跟其他本科系工程師討論技術、實作細節時，很常遇到聽不懂專有名詞的狀況，記得當時非常地氣餒，覺得自己很笨都聽不懂別人在說什麼。也嘗試過把專有名詞丟進 google，看了很多解釋的文章，雖然文章裡的每個字都看懂了，但真的要開始實作時，又不知道為什麼要選擇這樣的設計，始終處於一知半解的狀態。

那時候內心一直有個過不去的檻，是不是去把資工系的基礎科目補起來，上述一知半解的狀況就會緩解，是不是有一個本科系的學歷，就能跟那些本科系畢業的工程師平起平坐了。畢竟我和他們的差距就是四年資工系課程（＋研究所兩年）的差距。不然說到底，我也只是一個只會用套件，卻不懂套件的設計思維和底層運作、不懂電腦是怎麼被設計出來的程式碼工人。同時以台灣這麼看重學歷的職場環境，有了學歷也可以拓展出 web 以外的職涯發展路徑。

於是，我下了考資工所的決定。

### 準備過程

先寫在最前面，我是一邊上班一邊準備考試，準備時間大約是 2023 年一整年。

最一開始時想要自己自學準備，找了線上的學習資源，大部份是知名大學公開課，我是參考這兩個網站安排想要學習的課程：

- [Teach Yourself Computer Science](https://teachyourselfcs.com/)
- [CS自学指南](https://csdiy.wiki/)

然後下班回家之後就開始了看線上課程的生活，但是……過沒多久就失敗了，沒辦法持續下去。

為什麼會失敗呢？原因其實蠻簡單的：

- 這幾間知名大學的公開課（UC Berkeley, MIT…）對剛轉職不久的我來說太過困難，看影片時常常看不下去，或是都在放空。
- 下班之後很累，腦力可能已經燒光了，沒有餘力再繼續用腦。
- 讀書的進度太慢，趕不上在考試前全部唸完。
- 這些開放式課程對於實務上的技術進步和扎實基本功很有幫助，但對短期考試衝刺的功效甚微。

所以最後還是去報了補習班（大碩）。下面是我選擇的師資：

- 線性代數 - 黃子嘉
- 離散數學 - 林緯
- 資料結構 - 洪逸
- 演算法 - 林立宇
- 作業系統 - 洪逸
- 計算機組織 - 張凡

上述科目分成春季班跟秋季班上完，一季上三科，最後也有報名題庫班。基本上用來準備考試的教材以補習班的講義和題目為主。網路上都可以查到很多如何準備、如何唸書的心得，在這邊就不多贅述。

在準備考研究所的這一年時間，我把六科都唸過一遍，不是很紮實的那種，沒有複習也沒有寫考古題。所以在應考的時候，也有心裡準備會高機率落榜。

### 心得

一邊上班一邊準備真的太累了，平日早上去上班、晚上去上課，假日上一整天的課，基本上醒著的時候不是在上班就是在補習，剩下的空檔時間也不會想拿來複習考試科目，只會想要躺在床上睡覺，而且這樣的狀態持續了整整一年。建議如果想要跨考資工所的人還是專心全職準備比較能夠增加上榜的機率，如果一邊上班一邊準備的話，可能需要把準備時間拉長到兩年或三年，除非上班閒閒可以看書。

資工所考試當中最容易拿分的是數學，再來是資料結構，因為這幾個科目有唸課本、肯花功夫寫題目、累積一定的題海數量就有分數。演算法、作業系統、計算機組織的題目變化比較多樣、範圍較廣，甚至可能會考出課本以外的實務知識，沒有人敢肯定自己可以拿到多少分。但偏偏我最喜歡的科目是作業系統跟計算機組織，最討厭的科目是數學，對科目的喜惡也直接反應在了分數上，理想上考試的策略和自己對各種領域的喜好應該要能夠更清楚地區分，這樣在應考時的心態調整上會更好。

雖然最後並沒有成功考上資工所，但還是有蠻多收穫。比如：

- 知道了眾多資工的專業術語代表的意思是什麼，例如：process, scheduler, race condition, circular dependency, TLB, paging 等等，經過這一年之後，和其他工程師溝通的挫折感大幅降低。
- 好奇瀏覽器如何實作 javaScript engine，後來發現每一家瀏覽器解析出來的 byte code 其實都有點不太一樣，也就是說在某種程度上，自己不知不覺對 javaScript 和瀏覽器環境有更多的了解，也知道如果想要學更多，要往哪個方向學習。
- 開始思考如何最大化運用資源，應該算是學了作業系統之後應用在前端的成果。在寫前端時會開始考慮到 memory 的用量、發 request 時考慮網路的 traffic 狀況、根據 render process 選擇適合的 css property 等等。
- 開啟了對新領域的興趣，知道這個世界寫軟體的人不是只有前後端和 DevOps，還有很多自己可以學習的地方，比如寫 browser 也是寫軟體的一種。對嵌入式系統設計產生了蠻大的興趣，現在緩慢學習 C 語言中。
- 養成了每天看一點點新東西的習慣，可以慢慢地自己看懂一些比較深入解釋原理的文章、影片或書籍，終於不會看一看覺得好難喔想放棄的感覺。覺得就算第一次看不懂也沒關係，慢慢看或是以後有機會再回頭看，總是會懂的。
- 找回一開始寫程式的好奇心。最近各種技術自媒體、讀書會興起，還有各種教你如何面試、如何談薪水等等，好像不會這些就不是一個合格的工程師的感覺，搞得自己好焦慮。現在總算能夠比較不受到外界的影響，去重新堅定自己當初踏入程式的初衷——好奇電腦如何設計和運作。

至於要不要再考一次研究所？或是乾脆直接出國唸書呢？目前是還沒有這些想法，可能現階段的職涯也還沒遇到學歷上的門檻，暫時就先邊走邊看囉。
