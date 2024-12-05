## CODE PTIT AUTO SUBMIT VERSION 2.0

@Author: [n0xgg04](https://github.com/n0xgg04)

@Version: 2.0

Đảm bảo đã cài đặt sẵn NodeJS

### Installation:

- Install package

Cài đặt các lib cần thiết để chạy tool:

```sh
npm i -g yarn ts-node
```

```sh
yarn install
```

### Config

Mở file ``.env``
```
LIMIT_TASK=30
INIT_COUNT=0
DELAY_LOW=5
DELAY_HIGH=10
CODEPTIT_USERNAME=
CODEPTIT_PASSWORD=
COURSE_ID=759
COURSE_SUBMIT_ID=4
LANG_EXT=py
```

Mô tả:
- ``LIMIT_TASK`` : Số bài giới hạn, tool sẽ tự dừng nếu đạt giới hạn này
- ``INIT_COUNT`` : Bộ đếm khởi tạo (Đếm số lượng bài từ ?)
- ``DELAY_LOW`` và ``DELAY_HIGH`` : Thời gian nghỉ sau mỗi lần sub bài thành công (tính bằng phút), sẽ ngẫu nhiên từ ``DELAY_LOW`` tới ``DELAY_HIGH``
- ``CODEPTIT_USERNAME`` : Tên đăng nhập codeptit
- ``CODEPTIT_PASSWORD`` : Mật khẩu đăng nhập
- ``COURSE_ID`` : Mã môn học
- ``COURSE_SUBMIT_ID`` : Mã ngôn ngữ khi submit

 Để lấy mã môn học, bạn có thể truy cập trang chủ codeptit (danh sách bài), ấn F12 (Developer Tool/ Inspect) > Console và paste đoạn mã sau:
```js
JSON.stringify(Array.from(document.querySelectorAll('select#course option')).filter(i => !!i.getAttribute('value')).map(i => ({
    name: i.text,
    course_id: i.getAttribute('value')
})))
```

và ấn enter, kết quả có dạng 
```
'[{"name":"Lập trình hướng đối tượng - Nhóm 12","course_id":"744"},{"name":"Lập trình với Python - Nhóm 08","course_id":"759"},{"name":"Thuật toán và ứng dụng nâng cao - Nhóm THUẬT TOÁN NÂNG CAO - 2024","course_id":"732"}]'
```
Lấy ``course_id`` tương ứng với tên môn và để vào ``.env``
Nếu không thấy ``course_id`` của môn bạn cần, hãy để rỗng

Để lấy mã ngôn ngữ, hãy ấn vào 1 bài bất kỳ ở code ptit, và paste đoạn mã sau vào Console
```js
JSON.stringify(Array.from(document.querySelectorAll('select#compiler option')).filter(i => !!i.getAttribute('value')).map(i => ({
    name: i.text,
    lang_id: i.getAttribute('value')
})))
```

#### Một số id sẵn cho bạn

##### COURSE ID

- Python : 759
- Java OOP: 744
  
##### LANG ID
- JAVA 3
- PYTHON 4


### Run tool

Chạy tool bằng lệnh

```sh
yarn start
```

Khi chạy code, nếu hiển thị đúng số lượng bài đã làm, ví dụ:
```
Login success!
> Total problems:  292
> Incomplete problems:  117
> Complete problems:  175
Start auto submit code! Delay: 5 - 10 minutes
Submitting problemID : J05018, problemName: BẢNG ĐIỂM HỌC SINH
Submit code success!
Submitted 2/30 times
Waiting 9 minutes to submit next code!
```
thì là đã thành công, bạn chỉ cần treo máy.

Nếu hiển thị sai, thường là hiện 0, hãy thử lại bằng cách ấn ``Ctrl`` + C và start lại cho tới khi hiện đúng

##### Chúc bạn may mắn, không tự làm cẩn thận tạch môn đấy!
