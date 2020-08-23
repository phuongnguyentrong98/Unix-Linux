##User And Group 

I Mục Lục :
 1. Giới thiệu .
 2. User .
 3. Group .
 4. Quyền sử hữu user :
 
II User & Group  :

 1. Giới thiệu :
 - Trên hệ thống Linux, nhiều quy trình thường được sử dụng các quy trình cần quyền truy cập vào các tài nguyên cụ thể trên hệ thống Linux. 
 - Để xác định cách các tài nguyên này có thể được truy cập, sự khác biệt được tạo ra giữa các quy trình chạy ở chế độ hạt nhân và các quy trình chạy mà không có toàn quyền đối với hệ điều hành.
 - Bài đọc này giải thích cách thiết lập tài khoản người dùng và nhóm. Ngoài việc thiết lập tài khoản người dùng và nhóm, bạn cũng học cách kết nối tới dịch vụ xác thực bên ngoài, chẳng hạn như LDAP.
 
 2. Các loại người dùng khác nhau :
 - Trong chương này, bạn học cách tạo và quản lý tài khoản người dùng. Trước khi đi sâu vào chi tiết về quản lý người dùng, bạn tìm hiểu cách người dùng được sử dụng trong Linux
như thế nào.

 - Người dùng trong linux : 
     - Trên Linux, có hai cách để xem xét bảo mật hệ thống : bao gồm những người dùng có đặc quyền , và có những người dùng không có đặc quyền.
	 
	 - Người dùng có đặc quyền mặc định là root. Người dùng này tài khoản có toàn quyền truy cập vào mọi thứ trên máy chủ Linux và được phép làm việc trong không gian hệ thống không có giới hạn. Tài khoản người dùng root được dùng để thực hiện hệ thống các tác vụ quản trị và chỉ nên được sử dụng cho việc đó.
	 
	 - Đối với tất cả các tác vụ khác, nên sử dụng tài khoản người dùng không có đặc quyền. Để nhận thông tin về tài khoản người dùng, bạn có thể sử dụng lệnh id. Khi sử dụng lệnh này từ dòng lệnh, bạn có thể xem chi tiết về người dùng hiện tại. Bạn cũng có thể sử dụng nó trên các tài khoản người dùng khác để biết thông tin chi tiết về các tài khoản đó.

 2.1 Làm việc với root :
 
 - Trên tất cả các hệ thống Linux, theo mặc định có người dùng root, còn được gọi là superuser. Tài khoản này được sử dụng để quản lý Linux. Root có thể tạo ra các users khác trên hệ thống .
 
 - Đối với một số tác vụ, cần có đặc quyền root. Một số ví dụ như cài đặt phần mềm, quản lý người dùng và tạo phân vùng trên đĩa thiết bị. Nói chung, tất cả các tác vụ liên quan đến quyền truy cập trực tiếp vào thiết bị đều cần quyền của root.
 
 - Bởi vì tài khoản root rất hữu ích để quản lý môi trường Linux, một số người có thói quen đăng nhập trực tiếp bằng tài khoản root. Điều đó không được khuyến khích, đặc biệtkhông phải khi bạn đăng nhập vào môi trường đồ họa. Khi bạn đăng nhập với tư cách người chủ môi trường đồ họa, tất cả các tác vụ được thực thi cũng đang chạy dưới quyền root và điều đó có liên quan đến rủi ro bảo mật không cần thiết.
 
 2.2 Lệnh useradd : tạo tài khoản user 

```
useradd [Opption] login_name
```


 - Các options :
		 - -c : comment : tạo bí danh 
		 - -u : set user ID . Mặc định sẽ lấy ID tiếp theo để gán cho user 
		 - -d : chỉ định thư mục home 
		 - -g : chỉ định nhóm chính 
		 - -G : chỉ định nhóm phụ ( nhóm mở rộng )
		 - -s : chỉ định shell cho user sử dụng 
		 
 - Ví dụ tạo user Phuong với tên đầy đủ Nguyen Phuong 
    
![tao user](https://user-images.githubusercontent.com/68736233/89716141-b7502b00-d9d4-11ea-9e14-ba514b5f51f9.png)

 - User được tạo sẽ thuộc về nhóm Phuong và thư mục của user là /home/Phuong được tạo ra tự động .
 
 - Khi làm việc với các công cụ dưới dạng useradd, một số giá trị mặc định được giả định. Giá trị mặc định được đặt trong hai tệp cấu hình: /etc/login.defs và / etc / default /
useradd.
 
 2.3 Lệnh userdel : lệnh xóa user 
 - Cấu trúc :
 
```
userdel (-r) login_name
```

![del user](https://user-images.githubusercontent.com/68736233/89716515-c4224e00-d9d7-11ea-8956-34f1fa8d45ac.png)


 - Thư mục home của user sẽ không bị xóa khi sử dụng userdel login_name , để xóa cả thư mục home của user , sử dụng -r .
 - Khi xóa tài khoản user bằng lệnh userdel, dòng mô tả tương ứng của user trong các tập tin /etc/passwd và /etc/shadow cũng bị xóa.

 2.4 Lệnh su :
  
  - Lệnh su cho phép người dùng mở một cửa sổ dòng lệnh và từ dòng lệnh đó bắt đầu một trình bao phụ trong đó người dùng có danh tính khác.
  - Để thực hiện quản trịchẳng hạn, bạn có thể đăng nhập bằng tài khoản người dùng bình thường và nhập su để mở root shell.
  - Điều này mang lại lợi ích mà chỉ trong các đặc quyền của root shell mới được sử dụng. Nếu chỉ nhập lệnh su, thì tên người dùng root được ngụ ý. Nhưng su có thể được sử dụng để chạy các tác vụ với tư cách là người dùng khác. Nhập su Phuong để mở một vỏ con với tư cách là người dùng Phuong.
  - Khi sử dụng su như một người dùng bình thường, bạn sẽ được nhắc nhập mật khẩu và sau khi nhập, bạn đã có được thông tin đăng nhập của người dùng .
  - Cấu trúc lệnh : 
  
```
su options login_name
```


 2.5 Lệnh sudo : Cho phép bạn thiết lập một môi trường nơi các tác vụ cụ thể được thực thi với đặc quyền quản trị
 
 -Khi tạo người dùng Linux trong quá trình cài đặt, bạn có thể chọn cấp quyền của quản trị viên đối với người dùng cụ thể đó. Nếu bạn chọn làm như vậy, người dùng sẽ có thể sử dụng tất cả các lệnh của quản trị viên bằng sudo. Cũng có thể thiết lập sudo đặc quyền sau khi cài đặt. Để thực hiện điều đó một cách rất dễ dàng, bạn phải hoàn thành thủ tục hai bước đơn giản:
	 - 1. Làm cho tài khoản người dùng quản trị thành viên của bánh xe nhóm bằng cách sử dụng người dùng bánh xe usermod -aG.
	 - 2. Nhập visudo và đảm bảo dòng% wheel ALL = ALL
	 
![visudo](https://user-images.githubusercontent.com/68736233/89716747-d30a0000-d9d9-11ea-8634-78f8ee0d6552.png)

 2.6 Managing User Properties : Quản lý thuộc tính người dùng .
 - Đối với việc thay đổi thuộc tính người dùng, các quy tắc tương tự áp dụng như khi tạo tài khoản người dùng. Bạn có thể làm việc trực tiếp trong các tệp cấu hình bằng vipw hoặc bạn có thể sử dụng các công cụ dòng lệnh.
 - Tiện ích dòng lệnh cuối cùng để sửa đổi thuộc tính người dùng là usermod. Nó có thể được sử dụng để đặt tất cả các thuộc tính của người dùng như được lưu trữ trong / etc / passwd và / etc / shadow, cộng một số nhiệm vụ bổ sung, chẳng hạn như quản lý thành viên nhóm.
 - Trong tệp /etc/login.defs, các biến liên quan đến đăng nhập khác nhau được đặt . Tệp này được sử dụng bằng các lệnh khác nhau và nó liên quan đến việc thiết lập môi trường thích hợp cho người dùng mới. Đây là danh sách một số thuộc tính quan trọng nhất có thể được đặt từ /etc/login.defs:
	 - MOTD_FILE: Xác định tệp được sử dụng làm tệp "tin nhắn trong ngày". Trong tệp này, bạn có thể bao gồm các thông báo sẽ được hiển thị sau khi người dùng đã đăng nhập thành công vào máy chủ
	 - ENV_PATH: Xác định biến $ PATH, một danh sách các thư mục nên đã tìm kiếm các tệp thực thi sau khi đăng nhập.
	 - PASS_MAX_DAYS, PASS_MIN_DAYS và PASS_WARN_AGE: Xác định thuộc tính hết hạn mật khẩu mặc định khi tạo người dùng mới.
	 - UID_MIN: UID đầu tiên được sử dụng khi tạo người dùng mới.
	 - CREATE_HOME: Cho biết có hay không tạo thư mục chính cho những người dùng mới.
	 - USERGROUPS_ENAB: Đặt thành có để tạo nhóm riêng tư cho tất cả người mới người dùng. Điều đó có nghĩa là người dùng mới có một nhóm có cùng tên với người dùng làm nhóm mặc định của nó. Nếu được đặt thành không, tất cả người dùng được coi là thành viên của nhóm người dùng.
	 
 3. Creating and Managing Group Accounts :  Mỗi người dùng Linux phải là thành viên của ít nhất một nhóm. Trong phần này, bạn học cách quản lý cài đặt cho tài khoản nhóm Linux.

 3.1 Linux Group :
 - Người dùng Linux có thể là thành viên của hai loại nhóm khác nhau. Đầu tiên, có nhóm chính. Mọi người dùng phải là thành viên của một nhóm chính và chỉ có một nhóm chính. Khi tạo tệp, nhóm chính trở thành chủ sở hữu nhóm của các tệp này.
 - Người dùng cũng có thể truy cập tất cả các tệp mà nhóm chính của họ có quyền truy cập. Người dùng thành viên nhóm chính được đặt trong / etc / passwd
 - Bên cạnh nhóm chính bắt buộc, người dùng cũng có thể là thành viên của một hoặc nhiều nhóm phụ. Các nhóm phụ rất quan trọng để có quyền truy cập vào tệp. Nếu nhóm người dùng là thành viên có quyền truy cập vào các tệp cụ thể, người dùng sẽ có quyền truy cập vào các tệp này cũng vậy. 
 - Làm việc với các nhóm phụ rất quan trọng, đặc biệt là trong môi trường nơi Linux được sử dụng làm máy chủ tệp để cho phép mọi người làm việc cho các các phòng ban để chia sẻ tệp với nhau.
 - File /etc/group:
     - Là tập tin văn bản chứa thông tin về nhóm user trên máy. Mọi user đều có thể đọc tập tin này nhưng chỉ có root mới có quyền thay đổi.
	 
	 ![etc group](https://user-images.githubusercontent.com/68736233/89736964-af0cf400-da97-11ea-8e34-8aa001239410.png)

 - Mỗi dòng trong tập tin chứa thông tin về các nhóm user trên máy, định dạng của dòng gồm nhiều cột giá trị, dấu “:” được sử dụng để phân cách các cột. Ý nghĩa các cột giá trị như sau:
     - Cột 1 : Tên nhóm
	 - Cột 2 : Mật khẩu đã mã hóa 
		 - Để trống "" : không có mật khẩu 
		 - Dấu "*" : tài khoản bị tạm ngưng (disable).
	 - Cột 3 : Mã nhóm (gid)
	 - Cột 4 : Danh sách các user thuộc nhóm .
 
 3.2 Tạo group :
 - Giống như trường hợp tạo người dùng, cũng có các tùy chọn khác nhau để tạo nhóm. Các tệp cấu hình nhóm có thể được sửa đổi trực tiếp bằng cách sử dụng vigr hoặc lệnh groupadd .
 - Creating Groups with vigr :
	 - Với lệnh vigr, bạn mở giao diện trình chỉnh sửa trực tiếp trên / etc / group . Trong tệp này, các nhóm được xác định trong bốn trường cho mỗi nhóm.
	 - Các trường sau được sử dụng trong / etc / group: 
		 - Group name: chứa tên của nhóm 
		 - Group password: Một tính năng hầu như không được sử dụng nữa. Mật khẩu nhóm có thể được sử dụng bởi những người dùng muốn tham gia nhóm trên cơ sở tạm thời, do đó được phép truy cập vào các tệp mà nhóm có quyền truy cập.
		 - Group ID : ID nhóm 
		 - Members: Tại đây, bạn tìm thấy tên của những người dùng là thành viên của nhóm này như một nhóm phụ. Lưu ý rằng nó không hiển thị những người dùng là thành viên của nhóm này là nhóm chính của họ.
	
 - Creating Groups with groupadd  : Một phương pháp khác để tạo nhóm mới là sử dụng lệnh groupadd. Lệnh rất dễ sử dụng. Chỉ cần sử dụng groupadd theo sau là tên của nhóm bạn muốn thêm. Có một số tùy chọn nâng cao, điều quan trọng duy nhất trong số đó là -g, cho phép bạn chỉ định ID nhóm khi tạo nhóm.	
 
 ```
 groupadd (new group)
 ```
 
 - Option -g GID : định nghĩa nhóm vỡi mã GID 
 
 3.3 Lệnh groupmod : Sửa thông tin nhóm .
 - Cấu trúc lệnh :
 
```
groupmod options groupname
```


 - Option : 
	 - -g GID : sửa mã nhóm thành GID 
	 - -n groupnewname groupoldname : Sửa tên nhóm thành groupnewname 
 
 3.4 Lệnh groupdel : dùng để xóa nhóm .
 
 - Cấu trúc lệnh :
 
```
groupdel groupname
```

 3.5 Thêm / bớt 1 user vào ( ra khỏi ) nhóm :
 
 - Cấu trúc lệnh : 

```
gpasswd options groupname 
```

- Option :
	 - -a thêm user vào nhóm 
	 - -d xóa user khỏi nhóm
	 
 4. Thay đổi quyền sở hữu của người dùng :
 - Trong hệ điều hành Linux, mỗi file được đặt trong một nhóm sở hữu – group ownership và đặt bởi một chủ sở hữu. Chown là chữ viết tắt của “change owner” – đổi chủ sở hữu. Như tên gọi, chown command được dùng để thay đổi chủ sở hữu và nhóm chủ sở hữu của file, thư mục, links nếu bạn đang có quyền superuser của hệ thống Unix. Bài viết này sẽ hướng dẫn bạn cách sử dụng chúng. 
 - Nếu một người dùng bình thường muốn chỉnh sửa file, superuser có thể dùng lệnh chown command này để thay đổi ownership và cho phép họ chỉnh sửa 
 4.1 Quyền truy xuất : 
	 - Các loại quyền truy xuất : 
		 - Đọc (r : read): Cho phép đọc nội dung tập tin và xem nội dung thư mục bằng lệnh ls.
		 - Ghi (w : write): Cho phép thay đổi nội dung hoặc xóa tập tin. Đối với thư mục, quyền này cho phép tạo, xóa hoặc đổi tên tập tin mà không phụ thuộc vào quyền sở hữu trên tập tin chứa trong thư mục.
		 - Thực thi (x : execute): Cho phép thực thi chương trình, đối với thư mục, quyền này cho phép chuyển vào thư mục bằng lệnh cd.
	 - VD : 
		 - rwx : có toàn quyền 
		 - r-- : chỉ có quyền đọc 
		 - rw- : chỉ có quyền đọc và ghi
		 - --- : không có quyền gì 	 
![quyen](https://user-images.githubusercontent.com/68736233/89737903-f054d200-da9e-11ea-8d0a-0b0f4c266c09.png)

 4.2 Lệnh chown :
 - Cấu trúc lệnh : 

```
chown options ownerfile
```
 - Lệnh này được dùng để đổi owners (chủ sở hữu) của file và folder. Thông thường bạn cần có quyền root để làm lệnh này.
 - Lệnh chown này sử dụng rất đơn giản. Bạn chỉ cần nhớ trong lệnh có user và group được ngăn cách bằng dấu “:”, đầu tiên là user sau đó là group.
 - Câu lệnh dưới đây sẽ thay đổi quyền sở hữu của file hoặc folder nào đó:
 
 
```
chown -R user:group thu-muc
```

![chown](https://user-images.githubusercontent.com/68736233/89778575-f6e35800-db37-11ea-915d-96291b13c564.png)




*Questrions :

	1.What is the UID of user root?
	-0
	2. What is the configuration file in which sudo is defined?
	-/etc/sudoers
	3. Which command should you use to modify a sudo configuration?
	-visudo
	4. Which two files can be used to define settings that will be used when creating
	users?
	-etc/default/useradd và etc/login.defs
	5. How many groups can you create in /etc/passwd?
	- only 
	6. If you want to grant a user access to all admin commands through sudo, which
	group should you make that user a member of?
	-group wheel
	7. Which command should you use to modify the /etc/group file manually?
	-vigr
	8. Which two commands can you use to change user password information?
	- passwd and chage
	9. What is the name of the file where user passwords are stored?
	- etc/shadow
	10. What is the name of the file where group accounts are stored?
	- etc/group


 
