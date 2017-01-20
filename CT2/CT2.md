<a name="warp_Top"></a>
<details>
  <summary>_Warp list:_ </summary>
  [Top Page](#warp_Top)  
  [Đề bài](#warp_Statement)  
  [Nhận xét tổng quan](#warp_axiom)  
  [Nhận xét bài (a)](#warp_cmt_a)  
  [Solution câu (a)](#warp_sol_a)  
  [Nhận xét bài (b)](#warp_cmt_b)  
  [Solution câu (b)](#warp_sol_b)  
  [Tổng quát và mở rộng](#warp_Conclusion)  
  <pre>
  </pre>
</details>
# Chiếu Toán 2

## By Hoàng Bảo Phúc

<a name="warp_Statement"></a>
## Problem statement:
<details>
  <summary>_Original Problem statement_ (13 dòng)</summary>
  &emsp;Lo sợ trước các kỳ thi Con Bò, Con Heo, Minh Mê Mệt mất ngủ triền miên nên đến trễ trong buổi chào cờ đầu tuần.  
  &emsp;Dĩ nhiên cậu chàng bị đội Cờ Đen bắt sống và trói vào cột cờ ngay tại sân trường.  
  &emsp;Trong sân trường là hàng hà sa số (10<sup>9</sup>+7) chiếc ghế xanh bị vứt bỏ lại sau buổi lễ chào cờ.  
  &emsp;Bỗng cô Tú hiện ra và nói với Minh:  
  >&emsp;&emsp;“Này bé, ta và cháu chơi trò này. Người đầu tiên trong hai chúng ta sẽ chuyển một số ghế (không phải tất cả) vào kho ở góc đằng kia, sau đó người kia sẽ chuyển thêm một số ghế vào kho. Ta và cháu sẽ thay phiên nhau chuyển ghế. Quy tắc duy nhất là người đi sau không được chuyển nhiều ghế hơn người đi trước. Người thắng là người chuyển chiếc ghế cuối cùng vào kho. Nếu cháu thắng, ta sẽ xin thầy Lương thầy Lợi cho cháu miễn thi Con Bò, Con Heo. Nếu cháu thua, cháu sẽ phải về nhà bán dầu ăn Neptune. Cháu hay cô sẽ đi trước nào?”  
  
  &emsp;Có vẻ đây là một lần đánh cược quá hời với Minh Mê Mệt. Liệu cậu chàng có thể có một chiến lược tối ưu để được miễn thi cho dù ban đầu có bao nhiêu ghế ở sân trường đi chăng nữa ?  
  &emsp;Vụ đánh cược này quá dễ? Giờ cô Tú thay đổi quy luật: Mỗi lần chuyển, số ghế người sau chuyển không vượt quá hai lần số ghế người trước chuyển.
  <pre>
  </pre>
</details>

&emsp; &emsp; - Trên sân trường có N cái ghế (N &le; 10<sup>9</sup>+7). Hai người lần lượt luân phiên đưa ghế vào trong kho (người đầu tiên có thể đưa bất kì số ghế nào vào kho nhưng không phải tất cả). Hãy tìm ra 1 chiến lược tối ưu để bạn luôn là người đưa được cái ghế cuối cùng vào trong kho nếu:  
&emsp; a) Người đi sau không được chuyển nhiều ghế hơn người đi trước.  
&emsp; b) Người đi sau không được chuyển quá ```2 lần số ghế của người đi trước```  

<a name="warp_axiom"></a>
## Pre-thinking to get A simple "obvious but important" axiom:
* Dễ thấy rằng, trong trường hợp **a)**, nếu ở bước đầu tiên, ```số ghế người đi trước đưa vào``` &ge; ![Imgur](http://i.imgur.com/zjg5xgv.gif), ở bước tiếp theo người thứ hai sẽ ngay lập tức có thể đưa toàn bộ số ghế còn lại vào kho.  
&emsp;&emsp; => Vậy để tránh điều này xảy ra, ở bước đầu tiên người đi trước phải đưa vào phải ít hơn ![Imgur](http://i.imgur.com/zjg5xgv.gif) cái ghế.

* Tương tự, ta nhận thấy, trong trường hợp **b)**, ở bước đầu tiên người đi trước phải đưa vào ít hơn ![Imgur](http://i.imgur.com/8deh5qY.gif) cái ghế.

**_Tổng Quát: Nếu có tất cả N cái ghế, và ở mỗi bước người đi sau không được đưa vào quá ```K lần số ghế của người đi trước```, thì ở bước đầu tiên người đi trước phải di chuyển ít hơn ![Imgur](http://i.imgur.com/0e6hgEe.gif) cái ghế._**

_Chú thích: Kí hiệu |n| là phần nguyên của n._

<a name="warp_cmt_a"></a>
## Nhận xét cho bài (a)
* Khi 1 người lựa chọn đưa vào 1 cái ghế ở bước thứ i bất kì, tất cả các nước sau đó của cả 2 người sẽ BUỘC PHẢI LÀ ```Đưa vào 1 cái ghế```. Vì ở mỗi nước không thể di chuyển quá số ghế ở bước trước và không thể không di chuyển cái ghế nào.
* Khi điều này xảy ra, vì trò chơi chỉ có 2 người, nên việc lặp đi lặp lại thao tác ```Đưa vào 1 cái ghế``` không làm ảnh hưởng đến tính chẵn lẻ. Vậy nên chắc chắn người đưa vào 1 cái ghế mà khiến cho số ghế còn lại đang lẻ chuyển thành chẵn sẽ là người thắng cuộc (Vì 1 là số lẻ).

<a name="warp_sol_a"></a>
## Solution to Problem (a)
* Dễ nhận thấy nếu N là số lẻ, ta chỉ cần lựa chọn là người đi trước, và ở bước đầu tiên di chuyển vào 1 cái ghế, Theo lập luận (2) ở trên, chắc chắn ta sẽ là người thắng cuộc. Điều này cũng áp dụng nếu lượt hiện tại là lượt của mình và số ghế còn lại hiện tại là số lẻ.
* Nếu N là số chẵn có dạng (2<sup>K</sup>): Ta lựa chọn là người đi sau và làm theo chiến thuật sau (Nếu không thoả mãn chuyển sang bước sau):
  * Bước 1: Nếu "kết liễu" được đối thủ, phải "kết liễu" ngay lập tức.
  * Bước 2: Nếu đối thủ chọn 1 số lẻ => số ghế còn lại là số lẻ, đến lượt mình đi, trả về trường hợp trên.
  * Bước 3: Nếu đối thủ chọn 1 số chẵn, đến lượt mình đi, chọn số ghế NHỎ NHẤT CÓ THỂ để số ghế còn lại có dạng 2<sup>M</sup> (M&lt;K). Điều này đảm bảo mình sẽ không chết vì nếu đối thủ chọn số ghế là 2<sup>K-1</sup> thì đã bị "kết liễu" ở Bước 1. Vậy ta chỉ cần đưa vào số ghế sao cho số ghế còn lại là 2<sup>K-1</sup>. Số ghế ta đưa vào chắc chắn nhỏ hơn 2<sup>K-1</sup>. Lại có số ghế hiện tại có dạng 2<sup>M</sup>, quay trở lại bước đầu và lặp lại quá trình đến khi thắng.
* Nếu N là số có dạng (2<sup>K</sup>)*M (M là số lẻ): Ta lựa chọn là người đi trước, và làm theo chiến thuật sau:
  * Bước 1: Tìm số X thoả mãn tính chất sau:
    * X &le; |M/2|
    * (M-X) có dạng 2<sup>A</sup>
    * Có thể chứng minh số như vậy luôn tồn tại vì đó chính là số X nhỏ nhất thoả mãn điều kiện (2). Nó chắc chắn nhỏ hơn M/2 vì nếu viết M dưới dạng 2<sup>B</sup>-C (C < 2<sup>B-1</sup> vì nếu C &ge; 2<sup>B-1</sup> ta có thể viết nó dưới dạng 2<sup>B-1</sup> - C') thì có: X = 2<sup>B-1</sup>-C < 2<sup>B-1</sup>-(C/2) = M/2.
  * Bước 2: Đưa vào số ghế bằng 2<sup>K</sup> * X. Số ghế còn lại là 2<sup>K</sup> * (M-X) = 2<sup>K</sup> * 2<sup>A</sup> = 2<sup>K+A</sup>. Đưa về trường hợp 2<sup>K</sup> ở trên. Ta không thể chết do X &le; |M/2|.

**=> VẬY LÀ CHẮC CHẮN THẮNG TRONG MỌI TRƯỜNG HỢP. (PROBLEM A SOLVED)**

<a name="warp_cmt_b"></a>
## Nhận xét cho bài (b)
* Trường hợp K = 1 là trường hợp đặc biệt nên ta có thể giải theo cách trên, ở bài này K = 2, ta sẽ giải theo cách "Đệ quy", hay nói đúng hơn là quy về các trường hợp nhỏ hơn đã biết, từ đó suy ra công thức tổng quát cho bài toán.
* Phối hợp sử dụng nhận xét ở đầu bài để loại trừ tối đa số trường hợp có thể để dễ dàng xét.

<a name="warp_sol_b"></a>
## Solution to Problem (b)
_Chú thích: Ở đây, xét trường hợp giả sử cả 2 người đều biết chơi 1 cách tối ưu, nói cách khác là không "tự sát", nếu 1 người "tự sát", người kia ngay lập tức phải bỏ chiến thuật và "kết liễu" người đó. Vì vậy, một khi đã viết "Người đi trước thắng", nghĩa là dù người đi sau có đi thế nào đi nữa thì người đi trước vẫn có cách dồn người đi sau chết, và ngược lại._  
**Chú ý: Các trường hợp sau xét rất nhiều để dễ hiểu, bạn có thể đọc hết hoặc nếu hiểu rồi thì [skip](#skip_this)**
* Xét các trường hợp theo số ghế: (Và áp dụng nhận xét ở đầu bài) (Giả sử cả 2 người đều biết chơi tối ưu)
  * 2 ghế: Người đi trước chắc chắn thua do không thể đưa vào ít hơn ![Imgur](http://i.imgur.com/29xptJv.gif) cái ghế.
    * Kết luận: Người đi sau thắng.
  * 3 ghế: Người đi trước chắc chắn thua vì không thể đưa vào ít hơn ![Imgur](http://i.imgur.com/V4hRawt.gif) cái ghế.
    * Kết luận: Người đi sau thắng.
  * 4 ghế: Người đi trước phải đưa vào ít hơn ![Imgur](http://i.imgur.com/lRcKm7l.gif) cái ghế, hay nói cách khác là buộc phải đưa vào 1 cái ghế. Trả về bài toán 3 cái ghế, lúc này lượt đi tới sẽ là của người kia nên người kia sẽ thua.
    * Kết luận: Người đi trước thắng.
  * 5 ghế: Lập luận tương tự, người đi trước buộc phải đưa vào 1 cái ghế, đưa về bài toán 4 cái ghế, tới lượt người kia nên người kia thắng.
    * Kết luận: Người đi sau thắng.
  * 6 ghế: Lập luận tương tự, buộc phải đưa vào 1 ghế, đi trước chắc thắng
    * Kết luận: Người đi trước thắng.
  * 7 ghế: Người đi trước được chọn giữa đưa vào 1 hoặc 2 ghế:
    * Đưa vào 1 ghế: Đưa về bài toán 6 ghế, mình đi sau => Thua
    * Đưa vào 2 ghế: Đưa về bài toán 5 ghế, mình đi sau => Thắng
    * Kết luận: Người đi trước thắng vì là người ra quyết định, và có cách để thắng.
  * 8 ghế: Đưa về 6 ghế hoặc 7 ghế, đi sau => Dù thế nào cũng thua
    * Kết luận: Người đi sau thắng.
  * 9 ghế: Có thể đưa về 7 ghế hoặc 8 ghế, đi sau => Đưa về 8 ghế để thắng
    * Kết luận: Người đi trước thắng.
  * 10 ghế: Đưa về 7,8 hoặc 9, đi sau => Đưa về 8 để thắng
    * Kết luận: Người đi trước thắng.
  * 11 ghế: Đưa về 8,9 hoặc 10, đi sau => Đưa về 8, thắng
    * Kết luận: Người đi trước thắng.
  * 12 ghế: Đưa về 9,10 hoặc 11, đi sau => Kiểu gì cũng thua
    * Kết luận: Người đi sau thắng.
  * 13 ghế: 9,10,11,12 => Win (12)
    * Kết luận: Người đi trước thắng.
  * 14 ghế: 10,11,12,13 => Win (12)
    * Kết luận: Người đi trước thắng
  * ... (Lập luận tương tự đến khi có N cần thiết) (15,16,17 đi trước thắng, 18 đi sau thắng...)
<pre></pre>
<a name="skip_this"></a>
* Bằng cách suy luận như trên, ta có thể lần lượt tìm ra cách thắng ở tất cả các trường hợp.
* Ta có nhận xét: Nếu trong các trường hợp mình có thể "quy về" sau bước đầu tiên, có ít nhất 1 trường hợp người đi sau thắng thì mình sẽ thắng (Vì sau bước đầu tiên, chuyển về bài toán con mới thì mình sẽ là người đi sau). Vì tất cả các trường hợp ta xét ở đây là "Người đi sau sẽ thắng bất kể người trước chọn cái gì", ta thực sự không cần quan trọng việc nước đi đầu tiên của mình có thể ảnh hưởng (limit) đến nước đầu tiên của người kia dẫn đến việc chiến lược không có kết quả hay không.
* Chiến lược cụ thể: Mỗi khi có thể "kết liễu" đối thủ thì sẽ "kết liễu" ngay lập tức, không thì mỗi bước chọn số nhỏ nhất dẫn đến cái (Đi sau thắng) nhỏ tiếp theo.
* Kết luận: Ta cần phải có công thức tính các số hạng của dãy (Đi sau thắng). Với 2 số hạng đầu của dãy là 2 và 3, ta có thể làm được điều này.
* Công thức và chứng minh:
  * _Chú thích: GLW = Go Last Win._
  * Các trường hợp thắng là các trường hợp thoả mãn công thức:  
  * ![Imgur](http://i.imgur.com/gaTfNFT.gif)
    
  
<a name="warp_Conclusion"></a>
## Mở rộng
* Với các trường hợp K > 2 (trường hợp tổng quát), ta có thể lập luận tương tự như (b), rồi tìm ra công thức tổng quát cho bài toán.
