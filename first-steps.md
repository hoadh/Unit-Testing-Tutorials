# Unit Testing - Những bước chân đầu tiên

> “Hành trình vạn dặm bắt đầu từ một bước chân.” - Lão Tử

## Giới thiệu
Chất lượng công việc là một trong những yếu tố quan trọng xác định thành công của bạn tại nơi làm việc. Có nhiều cách để làm điều này trong lĩnh vực công nghệ phần mềm. Nhưng có một cách dễ dàng và hiệu quả là áp dụng kiểm thử. Lý do đơn giản là vì việc tạo mã chất lượng quan trọng hơn nhiều so với việc tạo ra một khối lượng lớn mã khó bảo trì và tồn tại nhiều lỗi.

Unit Test (Kiểm thử đơn vị) là một kỹ thuật kiểm thử hướng tới các đối tượng là những khối thành phần nhỏ nhất trong phần mềm (thường là các hàm hoặc phương thức). Đây là một trong những cấp độ kiểm thử đơn giản và có thể bắt đầu sớm trong vòng đời phát triển phần mềm. Thậm chí bạn có thể viết unit test trước khi viết mã. Tuy nhiên, đây không phải là một thuật ngữ mới trong lĩnh vực phần mềm.  Khái niệm unit test xuất hiện lần đầu trong ngôn ngữ lập trình Smalltalk vào những năm 1970. Đến nay, unit test gần như đã trở thành một chuẩn mực trong ngành bởi mục đích của nó là phục vụ yêu cầu nâng cao chất lượng sản phẩm phần mềm.

Đối với nhiều lập trình viên, dù mới vào nghề hay đã gạo cội thì unit test là một trong những kỹ năng không thể thiếu khi làm việc. Nếu bạn chưa từng nghe qua, hoặc chưa có điều kiện thực hành thì cũng bước những bước chân đầu tiên vào công việc thú vị này qua bài viết này nhé!

## Thuật ngữ

Trước hết, chúng ta lượt qua một vài từ khoá có thể được sử dụng trong bài viết này.

* Test case - ca kiểm thử hoặc trường hợp kiểm thử
* Expected value - Giá trị mong đợi
* Actual value - Giá trị thực tế
* Mock, Stub, Spy, Fake - Các chức năng được mô phỏng hoặc giả lập trong bộ kiểm thử
* SUT (System Under Test), CUT (Code Under Test), OUT (Object Under Test) - Là các đối tượng đang được kiểm thử. Như: hệ thống, mã, đối tượng.

## Thiết kế test case

Trong phần này, chúng ta sẽ tìm hiểu xem một test case như thế nào là tốt. Dựa vào các đặc tính đó, chúng ta sẽ tìm hiểu những nguyên tắc để có thể thiết kế và thực hiện được các test case tốt.

### Cấu trúc một test case

Các trúc mã mà chúng ta nên tuân thủ trong một test case là `cấu trúc AAA`.

Cấu trúc này có 3 thành phần:

* Arrange - Chuẩn bị dữ liệu cho test case hiện tại.
* Act - Thực hiện việc gọi phương thức/hàm để nhận được kết quả thực tế.
* Assert - So sánh giá trị mong đợi và giá trị thực tế nhận được ở bước trên. Kết quả của bước này là:
  * PASSED: nếu kết quả mong đợi và kết quả thực tế khớp nhau
  * FAILED: nếu kết quả mong đợi khác với kết quả thực tế

### Thành phần cố định (Fixture)

Là những thành phần được lặp đi lặp lại qua mỗi test case và có thể chia sẻ các thao tác chung giữa các test case này trong một bộ test. Ví dụ: thiết lập cấu hình hoặc chuẩn bị dữ liệu trước khi bộ test được thực thi, và dọn dẹp bộ nhớ sau khi hoàn thành. Thành phần cố định phải được đặt lên trên cùng của bộ kiểm thử.

### Đặc tính của một Unit Test tốt

Một ca kiểm thử tốt sẽ có những đặc tính sau đây:

* Dễ viết - Có thể bao quát được nhiều trường hợp kiểm thử mà không mất quá nhiều công sức
* Dễ đọc - Có thể mô tả được chính xác hành vi hoặc chức năng được kiểm thử
* Tự động hoá - Có thể thực thi lặp lại nhiều lần
* Dễ thực thi
* Thực thi nhanh
* Đồng nhất  - Luôn trả về cùng kết quả sau mỗi lần chạy (nếu không thay đổi mã nguồn bên trong)
* Cô lập - Có thể thực thi độc lập mà không phụ thuộc vào các thành phần khác trong hệ thống. *Bạn có thể tham khảo mục "Sử dụng Mockito" để làm rõ hơn ý này.*
* Khi kết quả kiểm thử thất bại (FAILED), có thể dễ dàng tìm ra giá trị mong đợi và nhanh chóng xác định được vấn đề

### Nguyên tắc viết kiểm thử

## Sử dụng JUnit

Hiện nay, JUnit được tích hợp và hỗ trợ ở phần lớn các IDE hiện tại cho Java. Việc sử dụng JUnit trong các dự án Java không khó. Các bạn có thể tìm hiểu cách cài đặt thư viện cho dự án của mình qua những hướng dẫn trên mạng.

Trong mục này, chúng ta sẽ cùng lượt qua những tính năng được hỗ trợ trong JUnit 5 - phiên bản mới nhất hiện nay.

### Các Annotation trong JUnit

Sơ đồ dưới đây thể hiện thứ tự thực hiện các phương thức khi được đánh dấu với annotion tương ứng:

![quá trình thực hiện](_img/junit_annotations_2.png)

Các annotaion `@BeforeAll`, `@BeforeEach`,`@AfterEach`, `@AfterAll` là những khối lệnh thực hiện chức năng là thành cố định.

### Assertions

Assertions là lớp chứa các phương thức hỗ trợ đánh giá các điều kiện trong kiểm thử.

So với phiên bản trước, JUnit 5 vẫn giữ các phương thức cũ và thêm một số phương thức mới tận dụng những tích năng của Java 8.

Dưới đây là danh sách những phương thức assertion có trong JUnit5.

#### assertTrue và assertFalse

Phương thức `assertTrue` được dùng để kiểm tra kết quả của điều kiện có bằng `true` hay không. Ví dụ:

```java
@Test
public void whenAssertingConditions_thenVerified() {
    assertTrue(10 > 5, "10 lớn hơn 5");
}
```
Ngược lại, phương thức `assertFalse` được dùng để kiểm tra kết quả của điều kiện có bằng `false` hay không.

```java
@Test
public void whenAssertingConditions_thenVerified() {
    assertTrue(5 > 10, "5 không lớn hơn 10");
}
```

#### assertEquals và assertNotEquals

Phương thức `assertEquals` được dùng để kiểm tra giá trị mong đợi và thực tế có bằng nhau hay không. Ví dụ:

```java
@Test
public void whenAssertingConditions_thenVerified() {
  	String actual = new String("CodeGym").toUpperCase();
  	String expected = "CODEGYM";
  	assertEquals(expected, actual);
}
```

Ngược lại, Phương thức `assertNotEquals` được dùng để kiểm tra giá trị mong đợi và thực tế có bằng nhau hay không. Chúng ta cập nhật lại ví dụ ở trên:

```java
@Test
public void whenAssertingConditions_thenVerified() {
  	// thay thế phương thức toUpperCase() thành toLowerCase()
  	String actual = new String("CodeGym").toLowerCase();
  	String expected = "CODEGYM";
  	assertNotEquals(expected, actual);
}
```

Với trường hợp các giá trị chúng ta đang so sánh thuộc kiểu Object, `assertEquals` và `assertNotEquals` sẽ gọi phương thức  `equals` để so sánh giá trị.

Có một điểm cần lưu ý nếu giá trị là kiểu số thực (`float` hoặc `double`). Trên thực tế,  có nhiều trường hợp mà giá trị số thực mong đợi và thực tế có thể chênh lệch với nhau trong khoảng chấp nhận được. Với tình huống này, phương thức `assertEquals` và `assertNotEquals` hỗ trợ tham số thứ ba là `delta` (bên cạnh `expected` và `actual`). Chúng ta cùng xem qua ví dụ dưới đây:

```java
@Test
public void whenAssertingConditions_thenVerified() {
    float actual = 12 / 3.0001f;
    float expected = 4;
    assertEquals(expected, actual, 0.001f);
}
```

Kết quả của phép chia 12 cho 3.001 thì sẽ là một số thực 3.9998667. Kết quả của ca kiểm thử ví dụ trên là **PASSED** vì chúng ta đã cho phép mức chênh lệch tối đa là 0.001.

#### assertArrayEquals

Phương thức `assertArrayEquals` có thể xác nhận mảng mong đợi và thực tế có bằng nhau hay không. Chúng ta cùng xem xét ví dụ dưới đây:

```java
public void whenAssertingArraysEquality_thenEqual() {
    char[] expected = { 'C', 'o', 'd', 'e', 'G', 'y', 'm' };
    char[] actual = "CodeGym".toCharArray();
 
    assertArrayEquals(expected, actual, "Mảng phải giống nhau");
}
```

#### assertSame và assertNotSame

Khu chúng ta muốn xác nhận giá trị mong đợi và thực tế tham chiếu đến cùng một đối tượng hay không, chúng ta phải dùng `assertSame ` hoặc `assertNotSame`:

```java
@Test
public void whenAssertingSameObject_thenVerified() {
    String actual = new String("CodeGym");
    String expected = "CodeGym";
  
    assertSame(expected, actual);
}
```

Kết quả của phương thức test trên là **FAILED** vì hai biến `actual` và `expected` đang tham chiếu đến hai đối tượng khác nhau trong bộ nhớ.

Chúng ta nên lưu ý về sự khác nhau giữa `assertSame` và `assertEquals` (đã tìm hiểu ở ví dụ trước):

* `assertEquals` chỉ quan tâm đến giá trị có bằng nhau không (thông qua phương thức `equals`) mà không cần biết hai giá trị được so sánh có phải cùng là một đối tượng hay không.
* `assertSame` sẽ trả về PASSED chỉ khi cả hai biến cùng tham chiếu đến một đối tượng.

####  assertIterableEquals

`assertIterableEquals` so sánh các giá trị được chứa bên trong hai đối tượng kiểu Iterable. Để trả về kết quả PASSED, hai iterable phải trả về bằng số phân tử, giá trị của các phần tử đó và cả vị trí của các phần tử. Hãy cùng xem ví dụ dưới đây:

```java
@Test
public void givenTwoLists_whenAssertingIterables_thenEquals() {
    Iterable<String> al = new ArrayList<>(asList("CodeGym", "Coding", "Bootcamp", "Java"));
    Iterable<String> ll = new LinkedList<>(asList("CodeGym", "Coding", "Bootcamp", "Java"));

    assertIterableEquals(al, ll);
}
```

Kết quả của test case trên là **PASSED**. Phương thức `assertIterableEquals` chỉ so sánh giá trị các phần tử bên trong mà không quan tâm đến việc các phần tử này đang được lưu trữ tại hai biến thuộc kiểu khác nhau (ArrayList và LinkedList).

####  assertThrows

Để có thể xác nhận được phương thức đang kiểm thử có ném ra một ngoại lệ hay không, chúng ta có thể sử dụng `assertThrows`. Giả sử chúng ta có một phương thức như sau:

```java
static void throwAnException() {
	  throw new IllegalArgumentException("Tham số không hợp lệ");
}

```

Dùng cách thức dưới đây để kiểm tra xem phương thức `throwAnExcepiont()` có ném ra một ngoại lệ hay không, và ngoại lệ đó có phải là `IllegalArgumentException` hay không:

```java
@Test
void whenAssertingException_thenThrown() {
    Exception e = assertThrows(IllegalArgumentException.class, () -> throwAnException());
    assertEquals("Tham số không hợp lệ", e.getMessage());
}
```

#### Các assertion khác
* assertLinesMatch
* fail
* assertNotNull và assertNull
* assertAll
* assertTimeout và assertTimeoutPreemptively

## Sử dụng Mockito (Mocking framework)

Khi xây dựng phần mềm, SUT sẽ phụ thuộc vào các thành phần bên ngoài như cơ sở dữ liệu, API, hệ thống file,... Các thành phần phụ thuộc này có thể chưa sẵn sàng hoặc thậm chí chưa tồn tại ở thời điểm chúng ta viết Unit Test. Ngay cả khi những thành phần này đã được chuẩn bị sẵn sàng thì việc thực thi một test case có phụ thuộc sẽ chậm hơn vì phải cần thời gian đợi và tương tác với thành phần bên ngoài.

Cô lập SUT là một trong những kỹ thuật giúp giải quyết vấn đề trên. Và lúc này, chúng ta sẽ phải cần đến các Mocking framework (tạm dịch là khung mô phỏng) để giả lập các thành phần bên ngoài, nhờ đó có thể cô lập và kiểm thử SUT dễ dàng hơn. Việc tìm hiểu cách thiết lập và sử dụng các mocking framework này là bước quan trọng giúp mở rộng Unit Test cho các hệ thống lớn và phức tạp.

Mockito là một mocking framework dành cho Java.

### Lợi ích sử dụng

* Đối tượng mô phỏng không gây phá vỡ cấu trúc mã nguồn khi đối tượng thật được thiết kế và triển khai.

###  Tạo đối tượng mô phỏng

Phương thức `mock()` cho phép chúng ta tạo đối tượng mô phỏng từ một class hoặc interface. Phương thức này không yêu cầu thêm gì khi sử dụng. Và nó có thể tạo các thuộc tính class mô phỏng hoặc các đối tượng mô phỏng cần dùng trong phương thức. Ví dụ dưới đây thể hiện cách tạo một đối tượng mô phỏng kiểu `UserRepository` (đã được định nghĩa trước):

```java
StockRepository stockRepository = mock(StockRepository.class);
```

### Mô phỏng hành vi

Sử dụng phương thức `when()` để mô phỏng hành vi của đối tượng. Để xác định kết quả thực hiện, chúng ta có thể sử dụng `thenReturn()` hoặc `thenThrow()`.

* `thenReturn()` trả về kết quả
* `thenThrow()` sẽ ném ra một ngoại lệ

```java
when(stockRepository.count()).thenReturn(100);
```

Nếu muốn trả về nhiều kết quả cho nhiều lần gọi, chúng ta sử dụng `thenReturn()` nhiều lần như sau;

```java
when(stockRepository.count())
  .thenReturn(50)
  .thenReturn(100)
  .thenReturn(200);

// Kết quả in ra màn hình sẽ là:
System.out.println(stockRepository.count()); // 50
System.out.println(stockRepository.count()); // 100
System.out.println(stockRepository.count()); // 200
```

### Kiểm chứng

Chúng ta có thể kiểm tra xem phương thức/hàm có được gọi hay không qua phương thức `verify()`.

```java
verify(stockRepository).count();
```

Mockito hỗ trợ những tham số giúp chúng ta có thể mở rộng khả năng kiểm chứng việc gọi phương thức như:

* Số lần gọi với `times()`
* Thời gian thực hiện với `timeout()`, giúp kiểm chứng thời gian thực hiện thuật toán có đảm bảo yêu cầu

Ví dụ:

```java
verify(stockRepository, times(2)).count(); 	// gọi 2 lần
verify(stockRepository, timeout(10)).count(); // 10 mili giây
```

### Kết hợp JUnit

Đây là đoạn mã ví dụ cách kết hợp Mockito và JUnit để viết mã kiểm thử đơn vị:

```java
@Test
public void tryMockitoMock() {
  StockRepository stockRepository = mock(StockRepository.class);

		when(stockRepository.count())
     .thenReturn(10);
 
    long stockCount = stockRepository.count();
  
    Assertions.assertEquals(10, stockCount);
    verify(stockRepository).count();
}
```

Ở phương thức trên, chúng ta mô phỏng hành vi lấy số lượng user thông qua phương thức `count()` được định nghĩa trong UserRepository. Khi `count()` được gọi, đối tượng mô phỏng sẽ trả về kết quả là `111` thay vì phải truy vấn vào cơ sở dữ liệu để lấy thông tin.

## Case Study

Dự án chúng ta thực hiện là một ứng dụng tra cứu danh mục đầu tư dành cho các nhà đầu tư cổ phiếu chứng khoán.

Ứng dụng cần có các tính năng sau:

1. Tra cứu giá các mã cổ phiếu đang đầu tư (dữ liệu được lấy về từ API miễn phí)
2. Quản lý danh sách các mã cổ phiếu đang quan tâm (bao gồm tìm kiếm theo mã, lưu mã vào danh sách quan tâm, xoá một mã nào đó khỏi danh sách)

Trước khi thực sự viết mã, hãy hình dung trong đầu và vẽ ra một bảng thiết kế bao gồm những interface, class và các phương thức có thể cần để thực hiện được ứng dụng này. Dựa vào bản thiết kế, hãy viết các unit test case cho ứng dụng.

### Hướng dẫn

#### Tạo một class mô phỏng với tên là StockDB

Để mô phỏng hành vi sau:

1. Lưu mã cổ phiếu (kiểu chuỗi) và trả về `true`
2. Lấy thông tin mã cổ phiếu và trả về giá trị kiểu chuỗi

Các bước thức hiện:

1. Tạo interface StockDB
2. Viết test case và code

#### Tạo class mô phỏng StockAPI

Các tình huống khi test

1. Phương thức cần test là `void` (không trả về dữ liệu)
2. Phương thức cần test gọi đến một phương thức khác cùng lớp
   Chức năng: Lưu danh sách mã cổ phiếu quan tâm/đang đầu tư (gửi request lên DB)

Hai tình huống trên có thể sử dụng `spy()` kết hợp `doReturn()`.

Nếu đây là lần đầu tiên bạn viết unit test, có lẽ sẽ gặp nhiều khó khăn. Nhưng đừng nản chí nhé! Hành trình phía trước sẽ còn ẩn chứa nhiều điều thú vị.

## Chặng đường tiếp theo

Cảm ơn bạn đã đồng hành cùng bài viết đến đây. Hy vọng những bước chân đầu tiên này sẽ mang lại nhiều ý nghĩa cho chặng đường học hỏi tiếp theo của bạn. Hãy tìm tòi và thực hành nhiều hơn để có thể làm chủ được kỹ năng Unit Test nói riêng và automation testing nói chung. Tới đây, chúng ta nên làm gì để học và thực hành hiệu quả hơn ở kỹ năng này?

Câu châm ngôn của mình là "Thế giới này thật là rộng lớn.. và có quá nhiều sách để đọc". Nên gợi ý đầu tiên luôn là đọc những đầu sách hay về Unit Test, Test-Driven Development và những chủ đề liên quan. Các bạn xem qua danh sách gợi ý bên dưới nhé!

### Sách nên tham khảo

### Website nên tham khảo

