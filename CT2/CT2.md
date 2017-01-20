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
</details>

Trên sân trường có N cái ghế (N &le; 10<sup>9</sup>+7). Hai người lần lượt luân phiên đưa ghế vào trong kho (người đầu tiên có thể đưa bất kì số ghế nào vào kho nhưng không phải tất cả). Hãy tìm ra 1 chiến lược tối ưu để bạn luôn là người đưa được cái ghế cuối cùng vào trong kho nếu:  
&emsp; a) Người đi sau không được chuyển nhiều ghế hơn người đi trước.  
&emsp; b) Người đi sau không được chuyển quá ```2 lần số ghế của người đi trước```  

## Pre-thinking and simple "obvious" fact:
* Dễ thấy rằng, trong trường hợp **a)**, nếu ở bước đầu tiên, ```số ghế người đi trước đưa vào``` &ge; ![Imgur](http://i.imgur.com/zjg5xgv.gif), ở bước tiếp theo người thứ hai sẽ ngay lập tức có thể đưa toàn bộ số ghế còn lại vào kho.  
&emsp;&emsp; => Vậy để tránh điều này xảy ra, ở bước đầu tiên người đi trước phải đưa vào phải ít hơn ![Imgur](http://i.imgur.com/zjg5xgv.gif) cái ghế.

* Tương tự, ta nhận thấy, trong trường hợp **b)**, ở bước đầu tiên người đi trước phải đưa vào ít hơn ![Imgur](http://i.imgur.com/8deh5qY.gif) cái ghế.

**_Tổng Quát: Nếu có tất cả N cái ghế, ở mỗi bước người đi sau không được đưa vào quá ```K lần số ghế của người đi trước```, thì ở bước đầu tiên người đi trước phải di chuyển ít hơn ![Imgur](http://i.imgur.com/0e6hgEe.gif) cái ghế._**
