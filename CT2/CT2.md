# Chiếu Toán 2

## By Hoàng Bảo Phúc

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

## Pre-thinking to get A simple "obvious but important" axiom:
* Dễ thấy rằng, trong trường hợp **a)**, nếu ở bước đầu tiên, ```số ghế người đi trước đưa vào``` &ge; ![Imgur](http://i.imgur.com/zjg5xgv.gif), ở bước tiếp theo người thứ hai sẽ ngay lập tức có thể đưa toàn bộ số ghế còn lại vào kho.  
&emsp;&emsp; => Vậy để tránh điều này xảy ra, ở bước đầu tiên người đi trước phải đưa vào phải ít hơn ![Imgur](http://i.imgur.com/zjg5xgv.gif) cái ghế.

* Tương tự, ta nhận thấy, trong trường hợp **b)**, ở bước đầu tiên người đi trước phải đưa vào ít hơn ![Imgur](http://i.imgur.com/8deh5qY.gif) cái ghế.

**_Tổng Quát: Nếu có tất cả N cái ghế, ở mỗi bước người đi sau không được đưa vào quá ```K lần số ghế của người đi trước```, thì ở bước đầu tiên người đi trước phải di chuyển ít hơn ![Imgur](http://i.imgur.com/0e6hgEe.gif) cái ghế._**

_Chú thích: Kí hiệu |n| là phần nguyên của n._

## Nhận xét cho bài (a)
* Khi 1 người lựa chọn đưa vào 1 cái ghế ở bước thứ i bất kì, tất cả các nước sau đó của cả 2 người sẽ BUỘC PHẢI LÀ ```Đưa vào 1 cái ghế```. Vì ở mỗi nước không thể di chuyển quá số ghế ở bước trước và không thể không di chuyển cái ghế nào.
* Khi điều này xảy ra, vì trò chơi chỉ có 2 người, nên việc lặp đi lặp lại thao tác ```Đưa vào 1 cái ghế``` không làm ảnh hưởng đến tính chẵn lẻ. Vậy nên chắc chắn người đưa vào 1 cái ghế mà khiến cho số ghế còn lại đang lẻ chuyển thành chẵn sẽ là người thắng cuộc (Vì 1 là số lẻ).

## Solution to Problem (a)
* Dễ nhận thấy nếu N là số lẻ, ta chỉ cần lựa chọn là người đi trước, và ở bước đầu tiên di chuyển vào 1 cái ghế, Theo lập luận (2) ở trên, chắc chắn ta sẽ là người thắng cuộc. Điều này cũng áp dụng nếu lượt hiện tại là lượt của mình và số ghế còn lại hiện tại là số lẻ.
* Nếu N là số chẵn có dạng (2<sup>K</sup>): Ta lựa chọn là người đi sau và làm theo chiến thuật sau (Nếu không thoả mãn chuyển sang bước sau):
  * Bước 1: Nếu "kết liễu" được đối thủ, phải "kết liễu" ngay lập tức.
  * Bước 2: Nếu đối thủ chọn 1 số lẻ => số ghế còn lại là số lẻ, đến lượt mình đi, trả về trường hợp trên.
  * Bước 3: Nếu đối thủ chọn 1 số chẵn, đến lượt mình đi, chọn số ghế NHỎ NHẤT CÓ THỂ để số ghế còn lại có dạng 2<sup>M</sup> (M&le;K). Điều này đảm bảo mình sẽ không chết vì nếu đối thủ chọn số ghế là 2<sup>K-1</sup> thì đã bị "kết liễu" ở Bước 1. Vậy ta chỉ cần đưa vào số ghế sao cho số ghế còn lại là 2<sup>K-1</sup>. Số ghế ta đưa vào chắc chắn nhỏ hơn 2<sup>K-1</sup>. Lại có số ghế hiện tại có dạng 2<sup>M</sup>, quay trở lại bước đầu và lặp lại quá trình đến khi thắng.
* Nếu N là số chẵn không có dạng (2^i)*k (k là số lẻ): Ta lựa chọn là người đi trước, và làm theo chiến thuật sau:
  
