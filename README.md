# Intro to AI lab2
**`0712245 高魁駿`**
## Environment:
- development tools:
    - IDE: Sublime text, cmd(window,python3)
    - Compile Option: python main.py
## Task Description
- the problem :
    find solutions of Minesweeper problems using Backtrack Search
- algorithm :
    MRV, LCV, Degree heuristic, Fowarding check
## My Experiment

<font size =4>**1. Test case solution**</font>
**X : Mine**   
**-1 : No mine**
![](https://i.imgur.com/4yMQnYA.png)    ![](https://i.imgur.com/VqxEhuz.png)    ![](https://i.imgur.com/cyTiVob.png)    ![](https://i.imgur.com/2oGdcXZ.png)

<font size =4>**2. 五種演算法和 Forward Checking 的比較**</font>

The data for all kinds of non-random searches for all answers are given below. All tests are performed five times, and then the time average is taken. Because there is no randomness in the search process, the process is always the same, the number of steps and the maximum stack size are always the same, and there is no problem with the average value. The dictionary used here is 6x6 boards with 16 hints (17 constraints), 20 variables, and 10 mines in total.


1. None indicates that there is no algorithm, the algorithm always selects the Variable with the highest natural order
2. LCV
3. DML means the algorithm of Degree Heuristic first, then MRV then LCV
4. MDL represents the algorithm of MRV first, Degree Heuristic then LCV

==**#Test case 1**==
| Algorithm        | Checking         | Time   | Steps |
|:---------------- |:---------------- |:------ |:----- |
| None             | None             | 0.2972 | 20174 |
| MRV              | None             | 0.1146 | 3995  |
| Degree Heuristic | None             | 0.3620 | 5754  |
| MDL              | None             | 0.2633 | 3549  |
| DML              | None             | 0.2642 | 3549  |
| LCV              | None             | 0.2732 | 12396 |
| None             | Forward Checking | 0.0239 | 781   |
| MRV              | Forward Checking | 0.0279 | 700   |
| Degree Heuristic | Forward Checking | 0.0309 | 352   |
| MDL              | Forward Checking | 0.0369 | 432   |
| DML              | Forward Checking | 0.0378 | 432   |
| LCV              | Forward Checking | 0.0279 | 675   |
![](https://i.imgur.com/hK5XJe1.png)

![](https://i.imgur.com/LUx8iLY.png)

==**#Test case 2**==
| Algorithm        | Checking         | Time   | Steps |
|:---------------- |:---------------- |:------ |:----- |
| None             | None             | 0.0239 | 30    |
| MRV              | None             | 0.0029 | 20    |
| Degree Heuristic | None             | 0.6862 | 10328 |
| MDL              | None             | 0.2213 | 3395  |
| DML              | None             | 0.2293 | 3395  |
| LCV              | None             | 0.4218 | 18410 |
| None             | Forward Checking | 0.0019 | 8     |
| MRV              | Forward Checking | 0.0030 | 7     |
| Degree Heuristic | Forward Checking | 0.0418 | 484   |
| MDL              | Forward Checking | 0.0199 | 74    |
| DML              | Forward Checking | 0.0109 | 74    |
| LCV              | Forward Checking | 0.0249 | 681   |
![](https://i.imgur.com/4wj5P9S.png)

![](https://i.imgur.com/Su9ytIg.png)

==**#Test case 3**==
| Algorithm        | Checking         | Time   | Steps  |
|:---------------- |:---------------- |:------ |:------ |
| None             | None             | 2.3876 | 165350 |
| MRV              | None             | 2.0994 | 54904  |
| Degree Heuristic | None             | 0.0050 | 30     |
| MDL              | None             | 1.1549 | 14063  |
| DML              | None             | 2.9661 | 44126  |
| LCV              | None             | 2.5042 | 121786 |
| None             | Forward Checking | 0.2324 | 9947   |
| MRV              | Forward Checking | 0.1466 | 3428   |
| Degree Heuristic | Forward Checking | 0.0030 | 9      |
| MDL              | Forward Checking | 0.0479 | 465    |
| DML              | Forward Checking | 0.3082 | 3631   |
| LCV              | Forward Checking | 0.0389 | 1161   |
![](https://i.imgur.com/MDvYCAc.png)

![](https://i.imgur.com/VQpuDHa.png)

==**#Test case 4**==
| Algorithm        | Checking         | Time    | Steps |
|:---------------- |:---------------- |:------- |:----- |
| None             | None             | 0.1705  | 10626 |
| MRV              | None             | 0.1197  | 2407  |
| Degree Heuristic | None             | 0.0170  | 186   |
| MDL              | None             | 0.0269  | 189   |
| DML              | None             | 0.0.249 | 187   |
| LCV              | None             | 1.3862  | 63874 |
| None             | Forward Checking | 0.0169  | 598   |
| MRV              | Forward Checking | 0.1466  | 3428  |
| Degree Heuristic | Forward Checking | 0.0030  | 9     |
| MDL              | Forward Checking | 0.0039  | 12    |
| DML              | Forward Checking | 0.0039  | 10    |
| LCV              | Forward Checking | 0.0629  | 1351  |

![](https://i.imgur.com/VSMtfSB.png)

![](https://i.imgur.com/eFDCPzr.png)

* **Foward checking benefit**
基本上從上面四組測資所列出之表格不難看出，只要有做fowarding，我們所使用的stack iteration 一定比較少，所跑出來的時間也比較少
* **LCV 的悲劇**
這種情況並不是必然，因為測資三的數據顯示 LCV 的效能沒那麼悲劇，效能和 None 好很多，但可能只是變數排列陣行的偶然。LCV 能否發揮取決於 Domain 的歧異度，但老師給的題目中只有{0,1}，導致各變數的 Domain 大小相差無幾，最終導致 LCV 的發揮仍然有限。
* **MRV 和 Degree Heiristic看狀況，LCV 效果有限**
承上所述， Minesweeper 這東西的變數長度實在有限，然而 Domain 大小卻是大相逕庭，這讓 MRV 有極大的發揮空間。因此在這個遊戲中 MRV 跟 Degree Heiristic基本上要看使用時機當你動一格constraint所影響周圍越大那MRV的功用會比較好 。比較 MDL 和 DML 的數據也可以證明這點。而當測資三那種圖時不能發現，當 Mine連載一起的時候更有 Degree Heiristic發揮的空間

## 心得
**Degree Heuristic**
我⾃⼰是對 Degree Heuristic 的性能抱有⼀點疑慮。沒有任何 Checking 的測資⼆實測數據顯⽰， Degree Heuristic 的發揮在第三四筆的時候發揮得特別好

我在想，在其他的遊戲裡⾯，如果牽涉到的鄰居的數量有較⼤的落差時，這個演算法是不是能有跟 MRV 媲美的效果呢？我有設計過幾個測資讓相鄰的 varirable 數量比較分散，確實演算法有比較好的效果，但總是沒辦法跟 MRV ⼀樣好。

**Checking 的時間問題**
其實從最後總結的圖表中不難看出，以踩地雷這個遊戲來說，fowarding占了影響整個時間的比例，但其實不難想，因為當我搜索的一個var的時候，利用fowarding向九宮格搜尋，計算其upper bound and lower bound，而每當改動其九宮格的值
就可以找出mine的位置，反而是LCV對於這中domain length比較少的遊戲可能影響不大，假如是像數獨那種domain比較大的遊戲我相信LCV可以幫助可速找到要填的值

