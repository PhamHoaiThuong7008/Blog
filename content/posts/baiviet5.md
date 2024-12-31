---
title: "Những điều cần biết về Java Stream API"
date: 2024-12-19
draft: false
---

Java Stream API được giới thiệu trong Java 8, là một trong những cải tiến lớn giúp tăng hiệu suất xử lý và đơn giản hóa mã nguồn trong Java. Stream API giúp bạn xử lý dữ liệu một cách hàm ý và hiệu quả, giúp cải thiện khả năng đọc và bảo trì mã nguồn. Trong bài viết này, tôi sẽ giải thích về Stream API, cách sử dụng nó và các tính năng quan trọng mà bạn nên biết khi làm việc với Java.

### **Stream API là gì?**
Stream API là một công cụ được thiết kế để xử lý các tập dữ liệu (như Collections, Arrays, v.v.) theo cách thủ tục (functional style). Stream API không thay đổi nguồn dữ liệu ban đầu mà chỉ cung cấp một cách để xử lý và trả về kết quả mới mà không làm thay đổi nguồn dữ liệu gốc. Cách tiếp cận này giúp mã nguồn của bạn ngắn gọn và dễ hiểu hơn so với các cách xử lý dữ liệu truyền thống.

### **Khái niệm cơ bản về Stream:**
1. **Stream không lưu trữ dữ liệu:** Stream chỉ hoạt động trên dữ liệu, không lưu trữ dữ liệu. Chúng chỉ mô tả các thao tác được thực hiện trên dữ liệu.
2. **Stream có thể được xử lý song song:** Bạn có thể sử dụng các Stream song song để tận dụng các lõi CPU, giúp tăng hiệu suất khi làm việc với các tập dữ liệu lớn.
3. **Stream có thể áp dụng các thao tác qua các phương thức như `filter()`, `map()`, `reduce()`, và `collect()`.**

### **Các thao tác với Stream:**

Stream API hỗ trợ các thao tác cơ bản như sau:

- **Intermediate operations:** Là các thao tác thay đổi Stream và trả về một Stream mới. Những thao tác này không được thực thi ngay lập tức mà chỉ khi một terminal operation được gọi.
    - `filter()`: Chọn các phần tử đáp ứng điều kiện.
    - `map()`: Biến đổi các phần tử của Stream.
    - `distinct()`: Loại bỏ các phần tử trùng lặp.

- **Terminal operations:** Là các thao tác cuối cùng, khi được gọi, nó sẽ thực thi và có thể trả về một giá trị cụ thể hoặc hiệu suất.
    - `forEach()`: Duyệt qua các phần tử và thực thi một hành động.
    - `collect()`: Chuyển đổi Stream thành một Collection (như List hoặc Set).
    - `reduce()`: Tổng hợp các phần tử thành một giá trị duy nhất.

### **Ví dụ sử dụng Stream API:**
Giả sử bạn có một danh sách các tên và bạn muốn lọc các tên bắt đầu bằng chữ "J" và in ra chúng. Thay vì sử dụng vòng lặp truyền thống, bạn có thể sử dụng Stream API:

```java
import java.util.Arrays;
import java.util.List;

public class StreamExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Jane", "Jack", "Jill");

        names.stream()  // Tạo một stream từ danh sách
             .filter(name -> name.startsWith("J"))  // Lọc các tên bắt đầu bằng "J"
             .forEach(System.out::println);  // In ra kết quả
    }
}

Kết quả của đoạn mã trên sẽ là:
John
Jane
Jack
Jill
```