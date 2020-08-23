# Essential-File-Management-Tools-Linux

I. MỤC LỤC :
 1. Giới thiệu
 2. Hệ thống file phân cấp trong Linux
 3. Liên kết trong linux
 4. Làm việc với Lưu trữ và Nén tệp
 
II. File Management :

1. Giới thiệu:

  - Linux là 1 hệ điều hành với hệ thống file phân cấp.
  - Bài viết này sẽ giới thiệu cho bạn các kỹ năng quản lý tệp cần thiết. Bạn tìm hiểu cách tổ chức hệ thống tệp Linux và cách bạn có thể làm việc với các tập tin và thư mục.
  - Ngoài ra bạn cũng sẽ học cách quản lý các liên kết và lưu trữ nén hoặc không nén. 

2. Hệ thống file phân cấp trong Linux: 
  2.1 File System Management :
  - Hệ thống file trong linux được tổ chức theo tiêu chuẩn cấp bậc của hệ thống tập tin Filesystem Hierarchy Standard ( FHS ). Tiêu chuẩn này định nghĩa mục đích của mỗi thư mục.

![hệ thống file](https://user-images.githubusercontent.com/68736233/89384200-f017a800-d727-11ea-8df3-2cace9061f1e.png)

  - Hình dưới đây là cấu trúc cây thư mục trong linux :

![file thumuc](https://user-images.githubusercontent.com/68736233/89384544-72a06780-d728-11ea-91b3-55513464d572.png)

  - Linux dùng ký tự ‘/’ để tách các đường dẫn ( khác với Windows sử dụng “\” để tách các đường dẫn) tất cả các tập tin thư mục điều được bắt đầu từ thư mục gốc ( / ), cũng không có kí tự ổ đĩa giống như Windows.
  - File system là một phương pháp lưu trữ hoặc tìm kiếm các tập tin trên một đĩa cứng ( trong một phân vùng ). 
  - Khác với Windows :
![wind](https://user-images.githubusercontent.com/68736233/89384737-b7c49980-d728-11ea-963c-e621e073207f.png)

  - Các thư mục được mô tả như sau :
  
		- /bin : Các chương trình cơ bản. Chứa các file binary của các tập lệnh trong Linux
		
		- /sbin : Tương tự như /bin, nhưng là những lệnh chỉ được dùng bởi quản trị hệ thống - tương đương root user.
		
		- /boot : Chứa nhân Linux để khởi động và các file system maps cũng như các file khởi động giai đoạn hai.
		
		- /dev : Chứa các tập tin thiết bị (CDRom, HDD, FDD….). Trong Linux, mỗi thiết bị đều có file đại diện và được đặt tên theo 1 Logic nhất định:
			- cdrom : đĩa CDRom / DVD
			- fd : Đĩa mềm
			- hd : Đĩa cứng IDE
			- sd : Đĩa cứng SCSI
			- st : Băng từ
			- tty : cổng giao tiếp (COM,...)
			- eth : card ethenet
			
        - /etc : Chứa các tập tin cầu hình hệ thống.
	
        - /home : Thư mục dành cho người dùng khác root.
	
		- /lib : Chứa các thư viện dùng chung cho các lệnh nằm trong /bin và /sbin. Và thư mục này cũng chứa các module của kernel.
		
		- /mnt : hoặc /media	Mount point mặc định cho những hệ thống file kết nối bên ngoài.
		
		- /opt : Thư mục chứa các phần mềm cài thêm.
		
		- /srv : Dữ liệu được sử dụng bởi các máy chủ lưu trữ trên hệ thống.
		
		- /tmp : Thư mục chứa các file tạm thời.
		
		- /usr : Thư mục chứa những file cố định hoặc quan trọng để phục vụ tất cả người dùng.
		
		- /var : Dữ liệu biến được xử lý bởi daemon. Điều này bao gồm các tệp nhật ký, hàng đợi, bộ đệm, bộ nhớ cache,…
		
		- /root : Các tệp cá nhân của người quản trị (root).
		
		- /proc : Sử dụng cho nhân Linux. Chúng được sử dụng bởi nhân để xuất dữ liệu sang không gian người dùng
		
 2.2 Các kiểu file :

  - Trên linux tất cả mọi thứ đều được xem dưới dạng là file. Có 3 loại file: file thông thường (Regular files), file thư mục (Directory files), file đặc biệt (Special files).
	 - File thông thường: một chương trình, file text, library, file nhạc …
	 - Thư mục: thành phần dùng để chứa các file khác (container).
	 - File đặc biệt: (device, socket, pipe, symbolic links …).	
	 - Các file ẩn trong Linux thường bắt đầu bằng dấu "." .
	 
 2.3 Đường dẫn : 
  - Có 2 loại đường dẫn :
	 - Đường dẫn tuyệt đối bắt đầu bằng "/" .
		 - Đường dẫn tuyệt đối của một tệp tin hay thư mục đều bắt đầu bởi thư mục gốc / (root) và theo cây, theo nhánh, cho đến thư mục hoặc tệp mà bạn mong muốn. Tóm lại, một đường dẫn tuyệt đối là đường dẫn bắt đầu bởi / (root).
		 
	 - Đường dẫn tương đối :
		 - Đối với đường dẫn tương đối thì chúng ta sử dụng không đòi hỏi phải bắt đầu từ / (root) mà có thể tiếp cận được với các thư mục hay tệp tin bên trong thư mục hiện hành (working directory). 
		 - Một đường dẫn tương đối thường bắt đầu với:	
			 - Tên của một thư mục hoặc tệp tin.
			 - Hệ điều hành Linux dùng ký hiệu “.” chỉ thư mục hiện hành và ký hiệu “..” chỉ thư mục mẹ của thư mục hiện hành.
			 
	 - Cách lệnh thông dụng đối với đường dẫn tương đối và tuyệt đối:


```
cd /     Di chuyển về thư mục gốc 
```	 


```
cd /etc/networks     Di chuyển đến 1 vị trí bất kì khi biết đường dẫn tuyệt đối
```
    

```
cd docs   hoặc   ./docs     Di chuyển đến thư mục con nằm trong thư mục mẹ hiện tại
```


```
cd ..     Di chuyển đến thư mục mẹ 
```


```
cd ../..     Di chuyển về thư mục mẹ 2 lần
```


```
cd   hoặc   cd ~     Đưa về home 
```


```
cd -     Quay về thư mục trước 
```

 2.4 Các lệnh kiểm tra tình trạng hiệu suất :
	 - Ram : 
	 
```	 
free -option
```

         - b : hiển thị theo bytes
	 - k : hiển thị theo kilobytes
	 - m : hiển thị theo megabytes
	 - g : hiển thị theo gigabytes
	 - tera : hiển thị theo terabytes
	 - h : hiển thị theo kiểu tự động gom theo khối dữ liệu .
		 

  - Khác với windows , Linux chia Ram thành Mem và Swap. Trong khi windows dồn dung lượng trong ram thì linux có thể chia sẻ với Swap khi bộ nhớ đã đầy điều này giúp tránh được hiện tượng tràn ram và không làm ảnh hưởng đến hiệu suất công việc đang thực hiện.


 - Cpu :



```
cat /proc/cpuinfo
```	 


![ram cpu](https://user-images.githubusercontent.com/68736233/89389654-e134f380-d72f-11ea-916a-f986b1f6256d.png)

	  
 2.5 Lệnh df : Df hiển thị dung lượng ổ đĩa có sẵn trên hệ thống files
  - Cấu trúc lệnh :
 
 
```
 df [OPTION] [FILE]
```


  - Nếu cần biết loại hệ thống file nào được sử dụng trên các ổ đĩa, hãy sử dụng tùy chọn -T, theo sau là đường dẫn file.
  - Nếu bạn muốn xem kích thước của một file cụ thể theo GB thay vì byte mặc định, hãy sử dụng đường dẫn -h 
 
![df](https://user-images.githubusercontent.com/68736233/89422202-3b00e200-d75f-11ea-8fd0-b87b544b06bb.png)

 2.6 Lệnh mkdir : 
  - Lệnh MKDIR trong Linux cho phép user được tạo thư mục rỗng trên hệ điều hành Linux. Với lệnh “mkdir” bạn có thể tạo đồng thời nhiều thư mục, cũng như set được quyền cho cả thư mục khi tạo ra.
  - Cú pháp lệnh :

```
mkdir (filename1) (filename2)
```


  - Để tạo 1 thư mục bao gồm thư mục cha ( chưa tồn tại ) chứa thư mục con ta sử dụng option -p để tạo thư mục cha và -v tạo thư mục con tại root:

![mkdir](https://user-images.githubusercontent.com/68736233/89423359-97183600-d760-11ea-8021-4486ae15f114.png)


  - Ngoài ra với option “-m“; option này chấp nhận format và giá trị permission (775,…). Nếu bạn dùng option “-m” mà không đi kèm giá trị phân quyền thì thư mục sẽ được tạo ra theo giá trị umask mặc định. Từ đó có thể tạo thư mục phân quyền .

 2.7 Danh sách tập tin và thư mục :
  - Trong khi làm việc với các tệp và thư mục, sẽ hữu ích nếu bạn có thể hiển thị nội dung của thư mục hiện tại. Để làm điều này, bạn có thể sử dụng lệnh ls. Nếu được sử dụng mà không có đối số, ls hiển thị nội dung của thư mục hiện tại. Một số đối số phổ biến làm cho làm việc với ls dễ dàng hơn.
  - Tổng quan về ls :
     
     
	 ```
	 ls -l
	 ```
	 
	 -Hiển thị một danh sách, bao gồm thông tin về các thuộc tính tệp, chẳng hạn như ngày tạo và quyền.
		 
	 ```
	 ls -a 
	 ```
	 
	 -Hiển thị tất cả các tệp, bao gồm các tệp ẩn.
		 
	 ```
	 ls -lrt
	 ```
	 
	 -Đây là một lệnh rất hữu ích. Nó hiển thị các lệnh được sắp xếp và ngày sửa đổi. Bạn sẽ thấy các tập tin được sửa đổi gần đây nhất trong danh sách này.
		 
	 ```
	ls -d 
	 ```
	 
	 -Hiển thị tên của các thư mục, không phải nội dung của tất cả các thư mục khớp với các ký tự đại diện đã được sử dụng với lệnh ls.
		 
	 ```
	 ls -R
	 ```
	 
	 
	 
	 -Hiển thị nội dung của thư mục hiện tại, thêm vào đó là tất cả các thư mục con của nó, đó là đệ quy(Recursively) xuống tất cả các thư mục con.
		 
  - Một tệp ẩn trên Linux là một tệp có tên bắt đầu bằng dấu chấm. Thử câu lệnh sau: touch .hidden. Sau đó gõ ls, bạn sẽ chưa thấy nó. Gõ ls –a, bạn sẽ thấy.
 
  - Khi sử dụng ls và ls -l, bạn sẽ thấy các tệp được mã hóa màu. Các màu khác nhau được sử dụng cho các loại tệp khác nhau giúp phân biệt giữa chúng dễ dàng hơn. Tuy nhiên, đừng tập trung quá nhiều vào chúng, vì màu sắc được sử dụng là kết quả của một cài đặt biến, chúng có thể khác nhau trong các vỏ Linux khác nhau hoặc trên các máy chủ Linux khác nhau.
	 
 2.8 Sao chép, di chuyển tập tin và thư mục :
  - Để tổ chức các tệp trên máy chủ của bạn, bạn sẽ thường xuyên sao chép các tệp. Lệnh cp giúp bạn làm như vậy.
  - Cú pháp cũng đơn giản. Sử dụng cp theo sau là file bạn muốn sao chép và đích đến nơi bạn muốn đạt bản sao.


```
cp file1 file2
```

  - Tất nhiên, lệnh trên giả sử rằng file của bạn nằm trong cùng thư mục mà bạn đang làm việc.
  - Ta có thể cùng lúc copy rất là nhiều file trên Linux vào thư mục đích đến. Bạn chỉ cần lưu ý tham số cuối cùng của dòng lệnh phải là một thư mục thực sự.

![copy](https://user-images.githubusercontent.com/68736233/89429121-5c65cc00-d767-11ea-975f-d530ff9d55a7.png)

  - Di chuyển các file : Sử dụng lệnh mv để di chuyển một file cụ thể vào một thư mục. 


```
mv file1 /(thư mục)
```


![mv1](https://user-images.githubusercontent.com/68736233/89429673-0f362a00-d768-11ea-8729-952f464282ca.png)

 - Ngoài ra bạn còn có thể sử dụng lệnh mv để thay đổi tên file và thư mục :
 
 
 
```
mv oldname newname
```


![mv2](https://user-images.githubusercontent.com/68736233/89430139-9aafbb00-d768-11ea-9d77-c96e899c264c.png)


 2.9 Xóa file hoặc thư mục với lệnh rm :
  - Cấu trúc lệnh : 
 
 
 
```
rm /path/file
rm /path/thu-muc
```


  - Để xóa file bạn chỉ cần thực hiện chỉ định đường dẫn file bạn muốn xóa với rm 
  - Để xóa 1 thư mục rỗng sử dụng option -d  cũng giống với sử dụng lệnh rmdir
 
```
rm -d thu-muc-rong
```


![xoa](https://user-images.githubusercontent.com/68736233/89431396-13634700-d76a-11ea-88ff-104cdb633d16.png)

 - Để xóa thư mục có chứa dữ liệu file và thư mục con sử dụng option '-r'
 - Nếu bạn yêu cầu option -i máy sẽ hỏi xác nhận xóa hoặc -f máy sẽ xóa không hỏi xác nhận.
 
![xoa thumuc](https://user-images.githubusercontent.com/68736233/89432819-c2545280-d76b-11ea-8503-a65d5e8c5212.png)

3. Liên kết trong linux :
- Khái niệm liên kết tồn tại trên UNIX khá lâu rồi. Khái niệm này hoàn toàn bao quát hơn khái niệm Shortcut bên Windows. Unix cho phép tạo một liên kết tắt để trỏ đến một file vật lí khác, nó có thể là một file hay một thư mục.
- Ở đây phát sinh 2 khái niệm là liên kết cứng và liên kết mềm.
- Ngoài ra còn có inode : Có thể hiểu trong một thư viện, tất cả các cuốn sách được sắp xếp theo thể loại, tên tác giả hoặc tên sách. Giống như một thư viện, tất cả các file trong hệ thống Linux được tổ chức để truy xuất và sử dụng hiệu quả. Inode là một thực thể hỗ trợ việc sắp xếp các file trong hệ thống Linux.

 3.1 Liên kết mềm :
  -File liên kết mềm chỉ chứa các thông tin của file vật lí mà nó trỏ đến, nó hoàn toàn không tham chiếu trực tiếp đến điểm nhập inode của file này. Khi bạn xóa file vật lí gốc, thì dĩ nhiên file liên kết hoàn toàn không còn ý nghĩa j nữa, trừ khi bạn khởi tạo lại file vật lí đã xóa. Nhưng nếu xóa file liên kết mềm thì không có nghĩa là file vật lí kia cũng bị xóa nốt!
Mọi thao tác như thêm, chỉnh sửa dữ liệu trong 2 file này hoàn toàn như nhau.

```
ln -s (thumuc) (file)
```


 - Lệnh này tạo liên kết mềm đến thư mục cần đến 
 - Câu lệnh " ls -l " sẽ cho ta biết thông tin chi tieest của file vừa liên kết.
 
![lk mem](https://user-images.githubusercontent.com/68736233/89438243-c768d000-d772-11ea-8f93-b13978aed2c5.png)

 3.2 Liên kết cứng :
  -Liên kết cứng sẽ tạo ra 1 file vật lí cùng trỏ đến mục nhạp inode của file vật lí gốc. 2 fle này hoàn toàn đồng đẳng với nhau. Nếu xóa file gốc thì dữ liệu hoàn toàn không bị mất, nó chỉ mất khi ko còn liên kết nào đến inode nữa. 
  -Tạo ra file0 -> tạo liên kết cứng trỏ file1 đến file0 

![lk cung](https://user-images.githubusercontent.com/68736233/89439993-35ae9200-d775-11ea-9b23-558154647a98.png)

  - Lưu ý  1 số đặc tính của liên kết cứng :
     - Nếu bạn xóa file0 thì file1 vẫn đọc được nội dung dữ liệu. Chỉ khi bạn xóa luôn cả 2 file thì hệ thống mới nhận ra rằng inode không còn tham chiếu đến liên kết cứng nào đó.
	 - Số liên kết vật lí liên kết đến file0 trước đó là 1, bây giờ đã tăng lên 2. Nó bao gồm liên kết đến chính nó (Liên kết này cũng là 1 liên kết cứng).
	 
 
  - Để xóa liên kết :

```
unlink (filelink)
```

![unlink](https://user-images.githubusercontent.com/68736233/89440661-254ae700-d776-11ea-8328-3bb7e7c62f3c.png)

4. Làm việc với Lưu trữ và Nén tệp :
 
 - Một nhiệm vụ quan trọng khác liên quan đến tệp là quản lý tài liệu lưu trữ và tệp nén. Để tạo một kho lưu trữ các tệp trên Linux, lệnh tar thường được sử dụng. Lệnh này ban đầu được thiết kế để truyền phát tệp vào băng mà không nén bất kỳ tệp nào. Nếu bạn cũng muốn nén các tệp, một công cụ nén cụ thể phải được sử dụng hoặc bạn cần chỉ định một tùy chọn nén tệp lưu trữ trong khi nó được tạo. Trong phần này, bạn tìm hiểu cách làm việc với tài liệu lưu trữ và tệp nén.
  
 4.1 Quản lý lưu trữ với "tar"
 
 - The Tape ARchiver (tar) được sử dụng để lưu trữ files. Mặc dù ban đầu được thiết kế để truyền phát files vào băng sao lưu, nhưng trong sử dụng hiện tại, tar được sử dụng chủ yếu để ghi files vào tệp lưu trữ. Bạn phải có khả năng thực hiện ba nhiệm vụ quan trọng với tar :
     - Tạo một kho lưu trữ
	 - Liệt kê nội dung của một kho lưu trữ
	 - Trích xuất một kho lưu trữ
	 
 4.1.1 Tạo kho lưu trữ :
 - Để tạo một kho lưu trữ, bạn sử dụng lệnh :


```
tar -cf archivename.tar (file-archive)
```


 - Để thêm file vào kho lưu trữ : 
 
```
tar -rvf /root/archivename.tar file
```


 
![tar](https://user-images.githubusercontent.com/68736233/89443646-c176ed00-d77a-11ea-9b1c-bdcd76296b45.png)

 4.1.2 Nén và giải nén :
  
  - TAR chỉ dùng để đóng gói các tập tin thành 1 khối, vì vậy chúng ta cần thêm các tùy chọn nén để có thể giảm tối đa kích thước tập tin. Các tập tin tarball thường được nén ở dạng GZ hoặc BZ2 hoặc LZMA.
  - Tùy chọn (option) :
     - x : giải nén dữ liệu 
	 - z : nén với gzip (.gz)
	 - j : nén với bunzip2 (.bz2)
	 - lzma : nén với lzma (.lzma)
	 - f : chỉ đến file lưu trữ sẽ tạo 
	 - v : hiển thị những tập tin đang làm việc lên màn hình 
	 - r : thêm tập tin vào file đã lưu trữ 
	 - u : cập nhật file có trong file lưu trữ 
	 - t : liệt kê file đang có trong file lưu trữ 
	 - delete : xóa file có trong file lưu trữ 



  - Nén bới gzip và hiển thị dung lượng :
  
![dungluong](https://user-images.githubusercontent.com/68736233/89447268-ea4db100-d77f-11ea-9b64-d369db21d0b2.png)
