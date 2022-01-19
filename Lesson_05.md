## **Tạo Database**
```sql
CREATE DATABASE Cinema
```
***

**1.Tạo bảng nhân viên**
```sql
CREATE TABLE employee(
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    date_of_birth DATE NOT NULL,
    gender ENUM ('Male', 'Female'),
    address TEXT NOT NULL,
    mobile VARCHAR(11) NOT NULL,
    email TEXT NOT NULL,
    position TEXT NOT NULL
)
```
***
**Insert nhân viên**
```sql
INSERT INTO `employee`(`id`, `name`, `date_of_birth`, `gender`, `address`, `mobile`, `email`, `position`) VALUES (1,'Thai','2000-01-01','Male','Ha Noi',01234567899,'thai@gmail.com','manager');
INSERT INTO `employee`(`id`, `name`, `date_of_birth`, `gender`, `address`, `mobile`, `email`, `position`) VALUES (2,'Khai','2000-02-02','Male','Ha Noi',01234568899,'khai@gmail.com','staff');
INSERT INTO `employee`(`id`, `name`, `date_of_birth`, `gender`, `address`, `mobile`, `email`, `position`) VALUES (3,'Cuong','2000-03-03','Male','Ha Noi',01234566899,'cuong@gmail.com','staff');
INSERT INTO `employee`(`id`, `name`, `date_of_birth`, `gender`, `address`, `mobile`, `email`, `position`) VALUES (4,'Dung','2000-04-04','Female','Ha Noi',01233567899,'dung@gmail.com','staff');
INSERT INTO `employee`(`id`, `name`, `date_of_birth`, `gender`, `address`, `mobile`, `email`, `position`) VALUES (5,'Trang','2000-05-05','Female','Ha Noi',01222567899,'huong@gmail.com','staff');
```
***
**2.Tạo bảng ca làm việc**
```sql
CREATE TABLE shift(
    id INT PRIMARY KEY,
    shift_type ENUM ('Sáng', 'Chiều', 'Full-Time'),
    start TIME NOT NULL,
    end TIME NOT NULL, 
    day DATE NOT NULL,
    salary_per_day BIGINT NOT NULL,
    id_employee INT NOT NULL,
    FOREIGN KEY (id_employee) REFERENCES employee(id)
)
```
***
**Thêm ca làm**
```sql
INSERT INTO `shift`(`id`, `shift_type`, `start`, `end`, `day`, `salary_per_day`, `id_employee`) VALUES (1,'Full-Time','8:00:00','22:00:00','2022-01-01',300000,1);
INSERT INTO `shift`(`id`, `shift_type`, `start`, `end`, `day`, `salary_per_day`, `id_employee`) VALUES (2,'Sáng','8:00:00','15:00:00','2022-01-01',100000,2);
INSERT INTO `shift`(`id`, `shift_type`, `start`, `end`, `day`, `salary_per_day`, `id_employee`) VALUES (3,'Chiều','15:00:00','22:00:00','2022-01-01',120000,3);
INSERT INTO `shift`(`id`, `shift_type`, `start`, `end`, `day`, `salary_per_day`, `id_employee`) VALUES (4,'Chiều','15:00:00','22:00:00','2022-01-01',150000,4);
INSERT INTO `shift`(`id`, `shift_type`, `start`, `end`, `day`, `salary_per_day`, `id_employee`) VALUES (5,'Sáng','15:00:00','22:00:00','2022-01-01',120000,5);
```
***
**3.Tạo bảng lương thưởng**
```sql
CREATE TABLE bonus(
    id INT PRIMARY KEY,
    bonus_reason TEXT NOT NULL,
    bonus_money BIGINT NOT NULL
)
```
***
**Thêm tiền thưởng**
```sql
INSERT INTO `bonus`(`id`, `bonus_reason`, `bonus_money`) VALUES (1,'KPI ngày vượt 100%',100000);
INSERT INTO `bonus`(`id`, `bonus_reason`, `bonus_money`) VALUES (2,'KPI tuần vượt 100%',500000);
```
***
**4.Tạo bảng lương phạt**
```sql
CREATE TABLE punish(
    id INT PRIMARY KEY,
    punish_reason TEXT NOT NULL,
    punish_money BIGINT NOT NULL
)
```
***
**Thêm tiền phạt**
```sql
INSERT INTO `punish`(`id`, `punish_reason`, `punish_money`) VALUES (1,'Đi làm muộn',20000);
INSERT INTO `punish`(`id`, `punish_reason`, `punish_money`) VALUES (2,'Không giữ vệ sinh chung',20000);
INSERT INTO `punish`(`id`, `punish_reason`, `punish_money`) VALUES (3,'KPI ngày dưới 80%',50000);
INSERT INTO `punish`(`id`, `punish_reason`, `punish_money`) VALUES (4,'KPI tuần dưới 80%',200000);
```
***
**5.Tạo bảng nhân viên_lương thưởng**
```sql
CREATE TABLE employee_bonus(
    id INT PRIMARY KEY,
    id_bonus INT NOT NULL,
    id_employee INT NOT NULL,
    bonus_number INT NOT NULL,
    bonus_date TEXT NOT NULL,
    FOREIGN KEY (id_bonus) REFERENCES bonus(id),
    FOREIGN KEY (id_employee) REFERENCES employee(id)
)
```
***
**Thêm thông tin nối nhân viên-thưởng**
```sql
INSERT INTO `employee_bonus`(`id`, `id_bonus`, `id_employee`,`bonus_number`,`bonus_date`) VALUES (1,1,1,2,'2022/01/01, 2022/01/10');
INSERT INTO `employee_bonus`(`id`, `id_bonus`, `id_employee`,`bonus_number`,`bonus_date`) VALUES (2,1,2,1,'2022/01/08, 2022/01/10');
INSERT INTO `employee_bonus`(`id`, `id_bonus`, `id_employee`,`bonus_number`,`bonus_date`) VALUES (3,2,3,3,'2022/01/01, 2022/01/08, 2022/01/15');
INSERT INTO `employee_bonus`(`id`, `id_bonus`, `id_employee`,`bonus_number`,`bonus_date`) VALUES (4,1,4,2,'2022/01/01, 2022/01/08, 2022/01/15');
INSERT INTO `employee_bonus`(`id`, `id_bonus`, `id_employee`,`bonus_number`,`bonus_date`) VALUES (5,1,5,2,'2022/01/01, 2022/01/08, 2022/01/15');
```
***
**6.Tạo bảng nhân viên_lương phạt**
```sql
CREATE TABLE employee_punish(
    id INT PRIMARY KEY,
    id_punish INT NOT NULL,
    id_employee INT NOT NULL,
    punish_number TEXT NOT NULL,
    punish_date DATE NOT NULL,
    FOREIGN KEY (id_punish) REFERENCES punish(id),
    FOREIGN KEY (id_employee) REFERENCES employee(id)
)
```
***
**Thêm thông tin nối nhân viên-phạt**
```sql
INSERT INTO `employee_punish`(`id`, `id_punish`, `id_employee`,`punish_number`, `punish_date`) VALUES (1,1,1,3,'2022/01/02, 2022/01/06,2022/01/07');
INSERT INTO `employee_punish`(`id`, `id_punish`, `id_employee`,`punish_number`, `punish_date`) VALUES (2,1,2,4,'2022/01/03, 2022/01/05');
INSERT INTO `employee_punish`(`id`, `id_punish`, `id_employee`,`punish_number`, `punish_date`) VALUES (3,1,3,5,'2022/01/06, 2022/01/16');
INSERT INTO `employee_punish`(`id`, `id_punish`, `id_employee`,`punish_number`, `punish_date`) VALUES (4,1,4,6,'2022/01/01, 2022/01/10');
INSERT INTO `employee_punish`(`id`, `id_punish`, `id_employee`,`punish_number`, `punish_date`) VALUES (5,1,5,5,'2022/01/01, 2022/01/10');
```
***
**7.Tạo bảng lương cơ bản**
```sql
CREATE TABLE salary(
    id INT PRIMARY KEY,
    id_employee INT NOT NULL,
    id_shift INT NOT NULL,
    shift_number INT NOT NULL,
    salary_per_month BIGINT NOT NULL,
    FOREIGN KEY (id_employee) REFERENCES employee(id),
    FOREIGN KEY (id_shift) REFERENCES shift(id)
)
```
***
**Thêm thông tin lương cơ bản**
```sql
INSERT INTO `salary`(`id`, `id_employee`, `id_shift`, `shift_number`, `salary_per_month`) VALUES (1,1,1,30,9000000);
INSERT INTO `salary`(`id`, `id_employee`, `id_shift`, `shift_number`, `salary_per_month`) VALUES (2,2,2,30,3000000);
INSERT INTO `salary`(`id`, `id_employee`, `id_shift`, `shift_number`, `salary_per_month`) VALUES (3,3,3,30,3600000);
INSERT INTO `salary`(`id`, `id_employee`, `id_shift`, `shift_number`, `salary_per_month`) VALUES (4,4,4,30,4500000);
INSERT INTO `salary`(`id`, `id_employee`, `id_shift`, `shift_number`, `salary_per_month`) VALUES (5,5,5,30,3600000);
```
***
**8.Tạo bảng tổng lương tháng**
```sql
CREATE TABLE full_salary(
    id INT PRIMARY KEY,
    id_salary INT NOT NULL,    
    id_employee_bonus INT NOT NULL,
    id_employee_punish INT NOT NULL,
    month TEXT NOT NULL,
    total_salary BIGINT NOT NULL,
    FOREIGN KEY (id_salary) REFERENCES salary(id),
    FOREIGN KEY (id_employee_bonus) REFERENCES employee_bonus(id),
    FOREIGN KEY (id_employee_punish) REFERENCES employee_punish(id)
)
```
***    
**Thêm thông tin tổng lương thực lĩnh**
```sql
INSERT INTO `full_salary`(`id`, `id_salary`, `id_employee_bonus`, `id_employee_punish`, `month`, `total_salary`) VALUES (1,1,1,1,'Lương Tháng 1/2022',9140000);
INSERT INTO `full_salary`(`id`, `id_salary`, `id_employee_bonus`, `id_employee_punish`, `month`, `total_salary`) VALUES (2,2,2,2,'Lương Tháng 1/2022',3020000);
INSERT INTO `full_salary`(`id`, `id_salary`, `id_employee_bonus`, `id_employee_punish`, `month`, `total_salary`) VALUES (3,3,3,3,'Lương Tháng 1/2022',5000000);
INSERT INTO `full_salary`(`id`, `id_salary`, `id_employee_bonus`, `id_employee_punish`, `month`, `total_salary`) VALUES (4,4,4,4,'Lương Tháng 1/2022',4580000);
INSERT INTO `full_salary`(`id`, `id_salary`, `id_employee_bonus`, `id_employee_punish`, `month`, `total_salary`) VALUES (5,5,5,5,'Lương Tháng 1/2022',3700000);

```
***
**9.Tạo bảng khách hàng**
```sql
CREATE TABLE customer(
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    birth DATE NOT NULL,
    gender ENUM ('Male', 'Female'),
    mobile VARCHAR(11) NOT NULL,
    email TEXT NOT NULL
)
```
***
**Thêm thông tin khách hàng**
```sql
INSERT INTO customer (id, first_name, last_name, birth, gender, mobile, email) values (1, 'Caril', 'Gilliatt', '2002-05-17', 'Male', '6785495941', 'cgilliatt0@rambler.ru');
INSERT INTO customer (id, first_name, last_name, birth, gender, mobile, email) values (2, 'Eilis', 'Cattrell', '1992-06-12', 'Male', '5522605021', 'ecattrell1@github.io');
INSERT INTO customer (id, first_name, last_name, birth, gender, mobile, email) values (3, 'Marney', 'MacCarlich', '1992-03-20', 'Male', '8625623638', 'mmaccarlich2@bluehost.com');
INSERT INTO customer (id, first_name, last_name, birth, gender, mobile, email) values (4, 'Carmelina', 'Cayle', '1990-06-10', 'Female', '3502916959', 'ccayle3@mail.ru');
INSERT INTO customer (id, first_name, last_name, birth, gender, mobile, email) values (5, 'Eloise', 'Hars', '1992-12-24', 'Female', '4226083153', 'ehars4@noaa.gov');
```
***
**10.Tạo bảng nhà sản xuất**
```sql
CREATE TABLE producer(
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    address TEXT NOT NULL
)
```
***
**Thêm thông tin NSX phim**
```sql
INSERT INTO producer (id, name, address) values (1, 'Browsezoom', '69442 Kingsford Center');
INSERT INTO producer (id, name, address) values (2, 'Jamia', '19 Bonner Crossing');
INSERT INTO producer (id, name, address) values (3, 'Livetube', '49 Talmadge Drive');
INSERT INTO producer (id, name, address) values (4, 'Riffwire', '0 Ludington Plaza');
INSERT INTO producer (id, name, address) values (5, 'Ozu', '094 Loeprich Center');

```
***
**11.Tạo bảng diễn viên**
```sql
CREATE TABLE actor(
    id INT PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL
)
```
***
**Thêm thông tin diễn viên**
```sql
INSERT INTO actor (id, first_name, last_name) values (1, 'Brad', 'Pitt');
INSERT INTO actor (id, first_name, last_name) values (2, 'Angelina', 'Jolie');
INSERT INTO actor (id, first_name, last_name) values (3, 'Patrick', 'Wilson');
INSERT INTO actor (id, first_name, last_name) values (4, 'Emma', 'Watson');
INSERT INTO actor (id, first_name, last_name) values (5, 'Meryl', 'Streep');
```
***
**12.Tạo bảng thể loại**
```sql
CREATE TABLE category(
    id INT PRIMARY KEY,
    name TEXT NOT NULL
)
```
***
**Thêm thông tin thể loại phim**
```sql
INSERT INTO `category`(`id`, `name`) VALUES (1,'Action');
INSERT INTO `category`(`id`, `name`) VALUES (2,'Horror');
INSERT INTO `category`(`id`, `name`) VALUES (3,'Romantic');
```
***
**13.Tạo bảng format**
```sql
CREATE TABLE format(
    id INT PRIMARY KEY,
    format TEXT NOT NULL
)
```
***
**Thêm format**
```sql
INSERT INTO `format`(`id`, `format`) VALUES (1,'2D');
INSERT INTO `format`(`id`, `format`) VALUES (2,'3D');
INSERT INTO `format`(`id`, `format`) VALUES (3,'4D');
```
***
**14.Tạo bảng phim**
```sql
CREATE TABLE film(
    id INT PRIMARY KEY,
    id_actor INT NOT NULL,
    FOREIGN KEY (id_actor) REFERENCES actor(id),
    id_category INT NOT NULL,
    FOREIGN KEY (id_category) REFERENCES category(id),
    id_producer INT NOT NULL,
    FOREIGN KEY (id_producer) REFERENCES producer(id),
    title TEXT NOT NULL,
    director TEXT NOT NULL,
    poster TEXT NOT NULL,
    description TEXT NOT NULL,
    length INT NOT NULL,
    rating ENUM('PG','G','PG-13','R','NC-17'),
    status ENUM('Release','Coming Soon')
)
```
***
**Thêm dữ liệu phim**
```sql
INSERT INTO `film`(`id`, `id_actor`, `id_category`, `id_producer`, `title`, `director`, `poster`, `description`, `length`, `rating`, `status`) VALUES (1,1,1,1,'World War Z','Marc Forster','https://cdn.tgdd.vn/Files/2021/04/01/1339988/top-10-phim-hay-va-noi-tieng-nhat-cua-tai-tu-brad-pitt-202104012143185762.jpg','The story revolves around the character Gerry Lane, a United Nations employee who travels around to protect the world when humanity is facing a strange disease.',116,'PG','Release');
INSERT INTO `film`(`id`, `id_actor`, `id_category`, `id_producer`, `title`, `director`, `poster`, `description`, `length`, `rating`, `status`) VALUES (2,2,3,2,'Mr.&Mrs.Smith','Doug Liman','https://i.bloganchoi.com/bloganchoi.com/wp-content/uploads/2021/09/phim-smith.jpg?fit=550%2C20000&quality=95&ssl=1','Mr. and Mrs. Smith is an action-adventure film that tells the love story of a mysterious assassin couple played by Angelina Jolie and Brad Pitt.',126,'G','Release');
INSERT INTO `film`(`id`, `id_actor`, `id_category`, `id_producer`, `title`, `director`, `poster`, `description`, `length`, `rating`, `status`) VALUES (3,3,2,3,'The Conjuring','James Wan','https://www.google.com/url?sa=i&url=https%3A%2F%2Fvi.wikipedia.org%2Fwiki%2F%25C3%2581m_%25E1%25BA%25A3nh_kinh_ho%25C3%25A0ng&psig=AOvVaw29KoCXaRXYBYleRyttHT_3&ust=1642662114027000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCKivurCfvfUCFQAAAAAdAAAAABAD','The Conjuring revolves around the story of the Perron family after moving back to an old mansion in the countryside. The Perron family's eagerness quickly fades as strange events keep happening, their daughters are regularly threatened at night by unseen forces.',112,'PG','Release');
```
***
**15.Tạo bảng nối format và phim**
```sql
CREATE TABLE film_format(
    id_film INT NOT NULL,
    FOREIGN KEY (id_film) REFERENCES film(id),
    id_format INT NOT NULL,
    FOREIGN KEY (id_format) REFERENCES format(id),
    PRIMARY KEY (id_film, id_format)
)
```
***
**Thêm thông tin nối format-phim**
```sql
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (1,1);
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (1,2);
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (2,1);
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (2,2);
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (2,3);
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (3,1);
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (3,2);
INSERT INTO `film_format`(`id_film`, `id_format`) VALUES (3,3);
```
***
**16.Tạo bảng trailer**
```sql
CREATE TABLE trailer(
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    id_film INT NOT NULL,
    video_trailer TEXT NOT NULL,
    FOREIGN KEY (id_film) REFERENCES film(id)
)
```
***
**Thêm dữ liệu trailer phim**
```sql
INSERT INTO `trailer`(`id`, `name`, `id_film`, `video_trailer`) VALUES (1,'World War Z','1','https://www.youtube.com/watch?v=ix33IBfTjUU');
INSERT INTO `trailer`(`id`, `name`, `id_film`, `video_trailer`) VALUES (2,'Mr.&Mrs.Smith','2','https://www.youtube.com/watch?v=CZ0B22z22pI');
INSERT INTO `trailer`(`id`, `name`, `id_film`, `video_trailer`) VALUES (3,'The Conjuring','3','https://www.youtube.com/watch?v=9YLiAy7CQhw');
```
***
**17.Tạo bảng phim_thể loại**
```sql
CREATE TABLE  film_category(
    id_film INT NOT NULL,
    id_category INT NOT NULL,
    FOREIGN KEY (id_film) REFERENCES film(id),
    FOREIGN KEY (id_category) REFERENCES category(id),
    PRIMARY KEY(id_film, id_category)
)
```
***
**Thêm dữ liệu nối thể loại - phim**
```sql
INSERT INTO `film_category`(`id_film`, `id_category`) VALUES ('1','1');
INSERT INTO `film_category`(`id_film`, `id_category`) VALUES ('2','3');
INSERT INTO `film_category`(`id_film`, `id_category`) VALUES ('3','2');
```
***
**18.Tạo bảng phim_diễn viên**
```sql
CREATE TABLE  film_actor(
    id_film INT NOT NULL,
    id_actor INT NOT NULL,
    FOREIGN KEY (id_film) REFERENCES film(id),
    FOREIGN KEY (id_actor) REFERENCES actor(id),
    PRIMARY KEY(id_film, id_actor)
)
```
***
**Thêm dữ liệu nối diễn viên - phim**
```sql
INSERT INTO `film_actor`(`id_film`, `id_actor`) VALUES (1,1);
INSERT INTO `film_actor`(`id_film`, `id_actor`) VALUES (2,2);
INSERT INTO `film_actor`(`id_film`, `id_actor`) VALUES (3,3);
```
***
**19.Tạo bảng phòng chiếu**
```sql
CREATE TABLE room(
    id INT PRIMARY KEY,
    name TEXT NOT NULL
)
```
***
**Thêm dữ liệu phòng chiếu**
```sql
INSERT INTO `room`(`id`, `name`) VALUES (1,'Room 1');
INSERT INTO `room`(`id`, `name`) VALUES (2,'Room 3');
INSERT INTO `room`(`id`, `name`) VALUES (3,'Room 5');
```
***
**20.Tạo bảng vị trí ghế**
```sql
CREATE TABLE seat(
    id INT PRIMARY KEY,
    seat_number TEXT NOT NULL,
    seat_row TEXT NOT NULL,
    status ENUM('Empty','Served')
)
```
***
**Thêm dữ liệu ghế ngồi**
```sql
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (1,1,'A','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (2,2,'A','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (3,3,'A','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (4,4,'A','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (5,5,'A','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (6,1,'B','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (7,2,'B','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (8,3,'B','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (9,4,'B','Empty');
INSERT INTO `seat`(`id`, `seat_number`, `seat_row`, `status`) VALUES (10,5,'B','Empty');
```
***
**Thêm bảng phòng + vé**
```sql
CREATE TABLE room_seat(
    id_room INT NOT NULL,
    FOREIGN KEY (id_room) REFERENCES room(id),
    id_seat INT NOT NULL,
    FOREIGN KEY (id_seat) REFERENCES seat(id),
    PRIMARY KEY (id_room, id_seat)
)
```
***
**Thêm dữ liệu ghế - phòng**
```sql
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,1);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,2);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,3);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,4);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,5);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,6);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,7);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,8);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,9);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (1,10);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,1);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,2);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,3);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,4);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,5);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,6);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,7);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,8);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,9);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (2,10);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,1);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,2);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,3);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,4);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,5);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,6);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,7);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,8);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,9);
INSERT INTO `room_seat`(`id_room`, `id_seat`) VALUES (3,10);

```
***
**21.Tạo bảng loại vé**
```sql
CREATE TABLE ticket_type(
    id INT PRIMARY KEY,
    type TEXT NOT NULL,
    price BIGINT NOT NULL
)
```
***
**Thêm dữ liệu loại vé**
```sql
INSERT INTO `ticket_type`(`id`, `type`, `price`) VALUES (1,'Normal',100000);
INSERT INTO `ticket_type`(`id`, `type`, `price`) VALUES (2,'V.VIP',200000);
```
***
**22.Tạo bảng discount**
```sql
CREATE TABLE discount (
    id INT PRIMARY KEY,
    discount FLOAT NOT NULL
)
```
***
**Thêm dữ liệu giảm giá**
```sql
INSERT INTO `discount`(`id`, `discount`) VALUES (1,0.1);
INSERT INTO `discount`(`id`, `discount`) VALUES (2,0.2);
```
***
**23.Tạo bảng hóa đơn khách hàng**
```sql
CREATE TABLE ticket_bill (
    id INT PRIMARY KEY,
    date_bill DATE NOT NULL,
    time_bill TIME NOT NULL,
    id_ticket_type INT NOT NULL,
    id_discount INT NOT NULL,
    FOREIGN KEY (id_discount) REFERENCES discount(id),
    FOREIGN KEY (id_ticket_type) REFERENCES ticket_type(id),
    numer_of_tickets INT NOT NULL,
    total_bill BIGINT NOT NULL
)
```
***
**Thêm dữ liệu hóa đơn khách hàng**
```sql
INSERT INTO `ticket_bill`(`id`, `date_bill`, `time_bill`, `id_ticket_type`, `id_discount`, `numer_of_tickets`, `total_bill`) VALUES (1,'2022-01-19','15:00:00',2,1,2,360000);
INSERT INTO `ticket_bill`(`id`, `date_bill`, `time_bill`, `id_ticket_type`, `id_discount`, `numer_of_tickets`, `total_bill`) VALUES (2,'2022-01-19','12:15:00',1,1,4,360000);
INSERT INTO `ticket_bill`(`id`, `date_bill`, `time_bill`, `id_ticket_type`, `id_discount`, `numer_of_tickets`, `total_bill`) VALUES (3,'2022-01-19','18:30:00',2,2,10,1600000);
```
***
**24.Tạo bảng vé**
```sql
CREATE TABLE ticket (
    id INT PRIMARY KEY,
    id_employee INT NOT NULL,
    id_customer INT NOT NULL,
    id_film INT NOT NULL,
    id_room INT NOT NULL,
    id_seat INT NOT NULL,
    cinema_address TEXT NOT NULL,
    date DATE NOT NULL,
    time_start TIME NOT NULL,
    time_end TIME NOT NULL,
    id_ticket_bill INT NOT NULL,
    FOREIGN KEY (id_ticket_bill) REFERENCES ticket_bill(id),
    FOREIGN KEY (id_employee) REFERENCES employee(id),
    FOREIGN KEY (id_customer) REFERENCES customer(id),
    FOREIGN KEY (id_film) REFERENCES film(id),
    FOREIGN KEY (id_room) REFERENCES room(id),
    FOREIGN KEY (id_seat) REFERENCES seat(id)
)
```
***
**Thêm dữ liệu soát vé**
```sql
INSERT INTO `ticket`(`id`, `id_employee`, `id_customer`, `id_film`, `id_room`, `id_seat`, `cinema_address`, `date`, `time_start`, `time_end`, `id_ticket_bill`) VALUES (1,2,1,1,1,1,'ABCDE','2022-01-19','12:15:00','13:35:00',2);
INSERT INTO `ticket`(`id`, `id_employee`, `id_customer`, `id_film`, `id_room`, `id_seat`, `cinema_address`, `date`, `time_start`, `time_end`, `id_ticket_bill`) VALUES (2,3,2,2,2,2,'ABCDE','2022-01-19','15:00:00','16:45:00',1);
INSERT INTO `ticket`(`id`, `id_employee`, `id_customer`, `id_film`, `id_room`, `id_seat`, `cinema_address`, `date`, `time_start`, `time_end`, `id_ticket_bill`) VALUES (3,4,3,3,3,3,'ABCDE','2022-01-19','18:30:00','20:15:00',3);
```
***
**25.Tạo bảng nhà cung cấp nguyên liệu**
```sql
CREATE TABLE supplier(
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    address TEXT NOT NULL,
    mobile VARCHAR(11) NOT NULL,
    bank_account_number TEXT NOT NULL
)
```
***
**Thêm dữ liệu nhà cung cấp**
```sql
INSERT INTO `supplier`(`id`, `name`, `address`, `mobile`, `bank_account_number`) VALUES (1,'Lets Popcorn','AAAAA','0334634665','666666666');
INSERT INTO `supplier`(`id`, `name`, `address`, `mobile`, `bank_account_number`) VALUES (2,'Coca-cola','BBBBB','0834556677','999999999');
```
***
**26.Tạo bảng phiếu nhập**
```sql
CREATE TABLE import_ticket(
    id INT PRIMARY KEY,
    id_employee INT NOT NULL,
    id_supplier INT NOT NULL,
    import_date DATE NOT NULL,
    imported_money BIGINT NOT NULL,
    FOREIGN KEY (id_employee) REFERENCES employee(id),
    FOREIGN KEY (id_supplier) REFERENCES supplier(id)
)
```
***
**Thêm dữ liệu phiếu nhập**
```sql
INSERT INTO `import_ticket`(`id`, `id_employee`, `id_supplier`, `import_date`, `imported_money`) VALUES (1,1,2,'2022-01-01',500000000);
INSERT INTO `import_ticket`(`id`, `id_employee`, `id_supplier`, `import_date`, `imported_money`) VALUES (2,2,1,'2022-01-01',50000000);
INSERT INTO `import_ticket`(`id`, `id_employee`, `id_supplier`, `import_date`, `imported_money`) VALUES (3,2,1,'2022-01-12',100000000);
INSERT INTO `import_ticket`(`id`, `id_employee`, `id_supplier`, `import_date`, `imported_money`) VALUES (4,3,2,'2022-01-14',100000000);
```
***
**27.Tạo bảng hàng nhập**
```sql
CREATE TABLE import_goods(
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    production_date DATE NOT NULL,
    expiration_date DATE
)
```
***
**Thêm dữ liệu hàng nhập**
```sql
INSERT INTO `import_goods`(`id`, `name`, `production_date`, `expiration_date`) VALUES (1,'Popcorn','2022-01-01','2023-01-01');
INSERT INTO `import_goods`(`id`, `name`, `production_date`, `expiration_date`) VALUES (2,'Drink','2022-01-01','2022-04-30');
```
***
**28.Tạo bảng chi tiết phiếu nhập**
```sql
CREATE TABLE detail_import_ticket(
    id_import_ticket INT NOT NULL,
    id_import_goods INT NOT NULL,
    quantity_of_goods INT NOT NULL,
    money_per_goods BIGINT NOT NULL,
    FOREIGN KEY (id_import_ticket) REFERENCES import_ticket(id),
    FOREIGN KEY (id_import_goods) REFERENCES import_goods(id),
    PRIMARY KEY(id_import_ticket, id_import_goods)
)
```
***
**Thêm dữ liệu chi tiết phiếu nhập**
```sql
INSERT INTO `detail_import_ticket`(`id_import_ticket`, `id_import_goods`, `quantity_of_goods`, `money_per_goods`) VALUES (1,1,200,20000);
INSERT INTO `detail_import_ticket`(`id_import_ticket`, `id_import_goods`, `quantity_of_goods`, `money_per_goods`) VALUES (2,2,50,10000);
INSERT INTO `detail_import_ticket`(`id_import_ticket`, `id_import_goods`, `quantity_of_goods`, `money_per_goods`) VALUES (3,3,100,10000);
INSERT INTO `detail_import_ticket`(`id_import_ticket`, `id_import_goods`, `quantity_of_goods`, `money_per_goods`) VALUES (4,4,100,20000);
```
***
**29.Tạo bảng menu**
```sql
CREATE TABLE menu (
    id INT PRIMARY KEY,
    name TEXT NOT NULL,
    type ENUM('Drink','Popcorn','Snacks'),
    price BIGINT NOT NULL
)
```
***
**Thêm dữ liệu menu**
```sql
INSERT INTO `menu`(`id`, `name`, `type`, `price`) VALUES (1,'Đồ Uống','Drink',50000);
INSERT INTO `menu`(`id`, `name`, `type`, `price`) VALUES (2,'Đồ Ăn','Popcorn',80000);
INSERT INTO `menu`(`id`, `name`, `type`, `price`) VALUES (3,'Đồ Ăn Nhỏ','Snack',25000);
```
***
**30.Tạo bảng hóa đơn ăn uống**
```sql
CREATE TABLE bill (
    id INT PRIMARY KEY,
    id_employee INT NOT NULL,
    id_menu INT NOT NULL,
    bill_date DATE NOT NULL,
    amount INT NOT NULL,
    FOREIGN KEY (id_employee) REFERENCES employee(id),
    FOREIGN KEY (id_menu) REFERENCES menu(id)
)
```
***
**31.Tạo bảng hóa đơn - menu**
```sql
CREATE TABLE menu_bill (
    id_bill INT NOT NULL,
    id_menu INT NOT NULL,
    FOREIGN KEY (id_bill) REFERENCES bill(id),
    FOREIGN KEY (id_menu) REFERENCES menu(id),
    PRIMARY KEY (id_bill, id_menu)
)
```
***
**32.Tạo bảng chi tiết hóa đơn**
```sql
CREATE TABLE detail_bill (
    id INT PRIMARY KEY,
    id_bill INT NOT NULL,
    id_menu INT NOT NULL,
    FOREIGN KEY (id_bill) REFERENCES bill(id),
    FOREIGN KEY (id_menu) REFERENCES menu(id),
    PRIMARY KEY (id_bill, id_menu),
    discount FLOAT NOT NULL,
    bill_money BIGINT NOT NULL
)
```



