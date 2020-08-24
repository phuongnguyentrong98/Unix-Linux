
# Scheduling Tasks
I Mục Lục :
1 Giới thiệu 
2 Định cấu hình cron
3 Managing the cron Service
4 Anacron

II Scheduling Tasks:

1 Giới thiệu :
-Trên máy chủ Linux, điều quan trọng là các tác vụ nhất định phải chạy vào những thời điểm nhất định. Điều này có thể được thực hiện bằng cách sử dụng các dịch vụ atd và crond
-Chúng có thể được cấu hình để chạy các tác vụ trong tương lai. Dịch vụ atd chỉ để thực thi các tác vụ trong tương lai một lần, dịch vụ crond dành cho các tác vụ thường xuyên lặp lại.

2 Định cấu hình cron để tự động hóa nhiệm vụ định kỳ:
-Trên hệ thống Linux, một số tác vụ phải được tự động hóa thường xuyên. Nó sẽ là một tùy chọn để định cấu hình từng quy trình với giải pháp dành riêng cho quy trình để xử lý nhiệm vụ lặp lại, nhưng điều đó sẽ không hiệu quả để giải quyết. Đó là lý do tại sao trên Linux dịch vụ cron được sử dụng như một dịch vụ chung để chạy các quy trình tự động .
- Dịch vụ cron bao gồm hai thành phần chính. Đầu tiên, đó là daemon cron. Daemon này xem xét từng phút để xem liệu có việc phải làm hay không. Điều này được xác định trong cấu hình cron, bao gồm nhiều tệp làm việc cùng nhau để cung cấp thông tin phù hợp cho đúng dịch vụ thời gian. Trong phần này, bạn học cách cấu hình cron.
- Các công việc trên được gọi là cronjob .
- Crontab (CRON TABLE) là một file chứa đựng trong nó các bảng biểu (schedule) và cronjob cần chạy cũng như thời gian chạy của nó.

3 Managing the cron Service:

3.1 Cài đặt cron:
- Câu lệnh : 

```
yum install cronie
```

3.2 Giám sát trạng thái hiện tại của dịch vụ crond
- Câu lệnh :

```
systemctl status crond
```

![Screenshot_1](https://user-images.githubusercontent.com/68736233/90992660-67c84c80-e5db-11ea-942a-e10f9c8c6c8a.png)

- Để hiển thị toàn bộ crontab của user hiện tại ta dùng:

```
crontab -l
```


3.3 Cấu trúc của crontab :
- Một crontab file có 5 trường xác định thời gian, cuối cùng là lệnh sẽ được chạy định kỳ, cấu trúc như sau:

![cautruc](https://user-images.githubusercontent.com/68736233/90992737-db6a5980-e5db-11ea-8173-e0fcf51ad2df.png)

- Nếu một cột được gán ký tự *, nó có nghĩa là tác vụ sau đó sẽ được chạy ở mọi giá trị cho cột đó.
- Các ký hiệu trong cấu trúc :   

![ky hieu](https://user-images.githubusercontent.com/68736233/90992776-0fde1580-e5dc-11ea-9f18-240c55e3622a.png)

3.4 Crontab :
- Tạo hoặc chỉnh sửa crontab

```
crontab -e 
```

- Xóa crontab :

```
crontab -r
```


- Ngoài ra thay vì sử dụng lệnh " crontab -e " để tạo và chỉnh sửa crontab , bạn có thể tạo file chứa các lệnh thực thi ( các cronjob ) và crontab trực tiếp đến file đó thể hệ thống thực hiện các tác vụ theo yêu cầu .

	 - B1 :
			![vi](https://user-images.githubusercontent.com/68736233/90993140-e6be8480-e5dd-11ea-8019-38b002f81831.png)
	
	 - B2 :
			![done](https://user-images.githubusercontent.com/68736233/90993173-fccc4500-e5dd-11ea-80a0-c49cf6775d9f.png)
			
	 - B3 :
			![nhan](https://user-images.githubusercontent.com/68736233/90993263-5fbddc00-e5de-11ea-8bde-32b4b9b2c3c5.png)
4. Anacron
- Để đảm bảo thực hiện công việc thường xuyên, cron sử dụng dịch vụ anacron. Dịch vụ này đảm nhận việc bắt đầu các công việc cron hàng giờ, hàng ngày, hàng tuần và hàng tháng, bất kể vào thời điểm chính xác nào.

![ana](https://user-images.githubusercontent.com/68736233/90993417-00140080-e5df-11ea-9425-3d37d663b2bf.png)

- Trong /etc/anacrontab, các công việc sẽ được thực thi được chỉ định trong các dòng chứa ba các trường, như được hiển thị trong hình 	
- Trường đầu tiên chỉ định tần suất thực hiện công việc, tính bằng ngày. Cột thứ hai chỉ định thời gian anacron đợi trước đó thực hiện công việc, và trong phần cuối cùng là lệnh sẽ được thực thi.

5 Questions :
	 -5.1 : Where do you configure a cron job that needs to be executed once every 2 weeks?
		 - 0 0 1,15 * * command
	 -5.2 : How do you specify the execution time in a cron job that needs to be executed twice every month, on the 1st and the 15th of the month at 2 p.m.?
		 - * 14 1,15 * * command
	 -5.3 : How do you specify cron execution time for a job that needs to run every 2 minutes on every day?
		 - */2 * * * * command
	 -5.4 : How do you specify a job that needs to be executed on September 19 and every Thursday in September?
		 - 0 0 19 9 4 command
	 -5.5 : Which three valid day indicators can you use to specify that a cron job needs to be executed on Sunday?
		 -
	 -5.6 : Which command enables you to schedule a cron job for user lisa?
		 - crontab -e -u lisa
	 -5.7 : How do you specify that user boris is never allowed to schedule jobs through cron?
		 -  /etc/cron.deny configuration files
	 -5.8 : You need to make sure that a job is executed every day, even if the server at execution time is temporarily unavailable. How do you do this?
		 - /etc/cron.{hourly|daily|weekly|monthly}
	 -5.9 : Which service must be running to schedule at jobs?
		 - systemctl status atd
	 -5.10 : Which command enables you to find out whether any current at jobs are scheduled for execution?
		 -
	 


	 

