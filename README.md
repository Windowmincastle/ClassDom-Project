# 👑Class Dom.👑
<p align="center"><img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/classdom.jpg" width="1000" height="300"/></p>

<hr>
 
### 🤭 팀원

<p align="center">
	<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/min.jpg" width="200" height="200"/>
	<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/seung.jpg" width="200" height="200"/>
	<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/su.jpg" width="200" height="200"/>
	<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/hye.jpg" width="200" height="200"/>
</p>

<div align="center">
	
|   &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;  &nbsp;  &nbsp; 🐶 김민성 [팀장]  &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;  &nbsp;  &nbsp;    |      &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;  &nbsp;  &nbsp; 🐱신승현  &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;  &nbsp;  &nbsp;    |      &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;  &nbsp;  &nbsp; 🐹김수연  &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;  &nbsp;  &nbsp;    |     &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;  &nbsp;  &nbsp; 🐰이혜진B  &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;  &nbsp;  &nbsp;   | 
|------------------------------------------|--------------------------------------|------------------------------------------|-----------------------------------|
 
</div>

<hr>

### 👨‍🏫 프로젝트 개요
  
  ClassDom 시스템은 프리랜서 교육 강사들이 효율적이고 효과적으로 교육 활동을 수행할 수 있도록 지원하기 위해 기획된 서비스입니다.
  
  서비스를 통해 강사들은 수강생 관리 업무에 소모되는 에너지를 줄이고, 고품질 강의 콘텐츠 제작에 집중할 수 있습니다.
  
  ClassDom 서비스는 프리랜서 교육 강사들이 수강생 관리에 드는 불필요한 에너지를 절감하고, 교육의 질을 높이며, 교육 기회를 확대하는 것을 목표로 합니다.

<hr>

### 👩‍🏫 서비스 목표

  1. 수강 생성 및 관리: 강사들이 쉽게 수강을 생성하고 체계적으로 관리할 수 있도록 지원.
  
  2. 교육 자료 관리: 강의 노트, 슬라이드, 동영상 등 다양한 교육 자료를 효율적으로 저장하고 공유.
  
  3. 수강생 출결 관리: 수강생의 출석 및 결석을 간편하게 관리
  
  4. 수강생 피드백 수집: 강의 후 수강생의 피드백을 체계적으로 수집하여 분석.
  
  5. 교육 기회 확대: 강사들이 더 많은 교육 기회를 가질 수 있도록 지원.
  
  6. 교육 품질 향상: 체계적인 관리와 피드백을 통해 지속적으로 교육 품질을 개선.

<hr>

### 🔨 기술 스택
<div>
<img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
<img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white">
<img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white">
<img src="https://img.shields.io/badge/mariaDB-003545?style=for-the-badge&logo=mariaDB&logoColor=white">
</div>

<hr>

### 📝 WBS

[WBS 바로가기](https://docs.google.com/spreadsheets/d/13AllHOgw_wXrzaS1d1lp7jXnGwdo9m9gy8zKgYyA6J0/edit?gid=1691021735#gid=1691021735)



<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/classdom%20project%20wbs.jpg"/>

<hr>

### ✅ 요구사항 정의서

[요구사항 정의서 바로가기](https://docs.google.com/spreadsheets/d/13AllHOgw_wXrzaS1d1lp7jXnGwdo9m9gy8zKgYyA6J0/edit?gid=0#gid=0)


![CLASSDOM 요구사항명세서](https://github.com/user-attachments/assets/deca3afb-e308-4a86-92ea-d876aa23ecd6)

<hr>

### 💻 DB 테이블 - ERD 및 DDL.

<p align="center"><img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/classdom%20project%20ERD.png"/></p>

<details>
<summary><b>CLASSDOM DDL</b></summary>
	
```sql
-- 회원 table 생성
CREATE TABLE `user` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `email` varchar(255) NOT NULL,
  `password` varchar(255) DEFAULT NULL,
  `name` varchar(255) NOT NULL,
  `phone_number` varchar(255) NOT NULL,
  `role` enum('학생','강사','관리자') NOT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  UNIQUE KEY `email` (`email`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌 table 생성
CREATE TABLE `course` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `description` varchar(8000) NOT NULL,
  `price` int(11) NOT NULL,
  `start_date` datetime NOT NULL,
  `end_date` datetime NOT NULL,
  `instructor_id` bigint(20) unsigned NOT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  `max_student` int(11) DEFAULT 30,
  `approval` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `user_id_fk` (`instructor_id`),
  CONSTRAINT `user_id_fk` FOREIGN KEY (`instructor_id`) REFERENCES `user` (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강의 table 생성
CREATE TABLE `lecture` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `content` varchar(255) DEFAULT NULL,
  `course_id` bigint(20) unsigned NOT NULL,
  `running_time` time NOT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `course_id_fk` (`course_id`),
  CONSTRAINT `course_id_fk` FOREIGN KEY (`course_id`) REFERENCES `course` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌질문 table 생성
CREATE TABLE `course_question` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `title` varchar(255) NOT NULL,
  `content` varchar(3000) DEFAULT NULL,
  `course_id` bigint(20) unsigned NOT NULL,
  `created_time` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) NOT NULL DEFAULT 'N',
  `writer` bigint(20) unsigned,
  PRIMARY KEY (`id`),
  KEY `course_cquestion_fk` (`course_id`),
  KEY `question_writer_fk` (`writer`),
  CONSTRAINT `course_cquestion_fk` FOREIGN KEY (`course_id`) REFERENCES `course` (`id`),
  CONSTRAINT `question_writer_fk` FOREIGN KEY (`writer`) REFERENCES `user` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌질문답변 table 생성
CREATE TABLE `course_response` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `content` varchar(3000) DEFAULT NULL,
  `c_question_id` bigint(20) unsigned NOT NULL,
  `created_time` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) NOT NULL DEFAULT 'N',
  `writer` bigint unsigned, 
  PRIMARY KEY (`id`),

  KEY `cquesiton_cresponse_fk` (`c_question_id`),
  KEY `question_response_fk` (`writer`),

  CONSTRAINT `cquesiton_cresponse_fk` FOREIGN KEY (`c_question_id`) REFERENCES `course_question` (`id`),
  CONSTRAINT `question_response_fk` FOREIGN KEY (`writer`) REFERENCES `user` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌과제 table 생성
CREATE TABLE `assignment` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `title` varchar(255) NOT NULL,
  `content` varchar(3000) DEFAULT NULL,
  `course_id` bigint(20) unsigned NOT NULL,
  `start_time` datetime DEFAULT NULL,
  `end_time` datetime DEFAULT NULL,
  `created_time` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) NOT NULL DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `course_assignment_fk` (`course_id`),
  CONSTRAINT `course_assignment_fk` FOREIGN KEY (`course_id`) REFERENCES `course` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌과제제출물 table 생성
CREATE TABLE `assignment_output` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `content` varchar(3000) DEFAULT NULL,
  `assignment_id` bigint(20) unsigned NOT NULL,
  `student_id` bigint(20) unsigned NOT NULL,
  `score` tinyint(4) DEFAULT 0,
  `feedback` varchar(300) DEFAULT '피드백 등록 전입니다.',
  `submit_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) NOT NULL DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `assignment_aoutput_fk` (`assignment_id`),
  KEY `cquestion_aoutput_fk` (`student_id`),
  CONSTRAINT `assignment_aoutput_fk` FOREIGN KEY (`assignment_id`) REFERENCES `assignment` (`id`),
  CONSTRAINT `assignment_student_fk` FOREIGN KEY (`student_id`) REFERENCES `user` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌시험 table 생성
CREATE TABLE `exam` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `course_id` bigint(20) unsigned NOT NULL,
  `title` varchar(255) NOT NULL,
  `content` varchar(3000) DEFAULT NULL,
  `exam_date` datetime NOT NULL,
  `limited_time` datetime DEFAULT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `exam_course_id_fk` (`course_id`),
  CONSTRAINT `exam_course_id_fk` FOREIGN KEY (`course_id`) REFERENCES `course` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌시험 제출물 table 생성
CREATE TABLE `exam_output` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `exam_id` bigint(20) unsigned NOT NULL,
  `student_id` bigint(20) unsigned NOT NULL,
  `content` varchar(3000) NOT NULL,
  `score` int(11) DEFAULT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `exam_output_exam_id_idx` (`exam_id`),
  KEY `exam_output_student_id_idx` (`student_id`),
  CONSTRAINT `exam_output_exam_id` FOREIGN KEY (`exam_id`) REFERENCES `exam` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION,
  CONSTRAINT `exam_output_student_id` FOREIGN KEY (`student_id`) REFERENCES `user` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 결제수단 table 생성
CREATE TABLE `payment_method` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `student_id` bigint(20) unsigned NOT NULL,
  `card_category` varchar(45) DEFAULT NULL,
  `card_number` char(16) DEFAULT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `payment_method_student_id_idx` (`student_id`),
  CONSTRAINT `payment_method_student_id` FOREIGN KEY (`student_id`) REFERENCES `user` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 강좌 수강 table 생성
CREATE TABLE `course_register` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `student_id` bigint(20) unsigned DEFAULT NULL,
  `course_id` bigint(20) unsigned DEFAULT NULL,
  `completed_state` char(1) DEFAULT 'N',
  `created_time` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `course_register_course_id_idx` (`course_id`),
  KEY `course_register_student_id_idx` (`student_id`),
  CONSTRAINT `course_register_course_id` FOREIGN KEY (`course_id`) REFERENCES `course` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION,
  CONSTRAINT `course_register_student_id` FOREIGN KEY (`student_id`) REFERENCES `user` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 결제 table 생성
CREATE TABLE `payment` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `register_id` bigint(20) unsigned DEFAULT NULL,
  `payment_id` bigint(20) unsigned DEFAULT NULL,
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `register_id_idx` (`register_id`),
  KEY `payment_id_idx` (`payment_id`),
  CONSTRAINT `payment_ibfk_1` FOREIGN KEY (`register_id`) REFERENCES `course_register` (`id`),
  CONSTRAINT `payment_ibfk_2` FOREIGN KEY (`payment_id`) REFERENCES `payment_method` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 리뷰 table 생성
CREATE TABLE `review` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `course_id` bigint(20) unsigned DEFAULT NULL,
  `student_id` bigint(20) unsigned DEFAULT NULL,
  `content` text DEFAULT NULL,
  `star` int(11) DEFAULT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `course_id_idx` (`course_id`),
  KEY `student_id_idx` (`student_id`),
  CONSTRAINT `review_ibfk_1` FOREIGN KEY (`course_id`) REFERENCES `course` (`id`),
  CONSTRAINT `review_ibfk_2` FOREIGN KEY (`student_id`) REFERENCES `user` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 출결 table 생성
CREATE TABLE `attendance` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `student_id` bigint(20) unsigned DEFAULT NULL,
  `lecture_id` bigint(20) unsigned DEFAULT NULL,
  `state` char(1) DEFAULT 'N',
  `view_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`),
  KEY `student_id_idx` (`student_id`),
  KEY `lecture_id_idx` (`lecture_id`),
  CONSTRAINT `attendance_ibfk_1` FOREIGN KEY (`student_id`) REFERENCES `user` (`id`),
  CONSTRAINT `attendance_ibfk_2` FOREIGN KEY (`lecture_id`) REFERENCES `lecture` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- F&A table 생성
CREATE TABLE `fa` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `title` varchar(255) DEFAULT NULL,
  `content` text DEFAULT NULL,
  `created_date` datetime DEFAULT current_timestamp(),
  `del_yn` char(1) DEFAULT 'N',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```
</details>

<hr>

### 📚 주요 프로시저

[전체 프로시저 바로가기](https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/integrated_procedure/integrated_procedure.sql)

<details>
<summary><b>👩‍💻회원</b></summary>
<div>
<details>
<summary><b>1. 회원가입</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE user_join(in emailInput varchar(255), in pwInput varchar(255), in nameInput varchar(255), in PhoneInput varchar(255), in roleInput enum('학생', '강사', '관리자') )
BEGIN
  insert into user(email, password, name, phone_number, role ) values (emailInput, pwInput, nameInput, PhoneInput, roleInput);
END
// DELIMITER ;
 ```
</details>
<details>
<summary><b>2. 회원조회</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE user_search(in email varchar(255))
BEGIN
  select * from user where email = email;
END
// DELIMITER ;
 ```
</details>
<details>
<summary><b>3. 회원정보수정</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE user_modify(in userEmail varchar(255), in userPw varchar(255), in userName varchar(255), in userPhone varchar(255))
BEGIN
  declare userId bigint;
  select id into userId from user where email = userEmail and password = userPw;
  if userId is null then
    select '아이디/비밀번호가 틀렸습니다.';
  else 
    update user set name = userName, phone_number = userPhone where id=userId;
  select '변경이 완료되었습니다.', email, password, name, phone_number from user where id = userId;
  end if;
END
// DELIMITER ;
```
</details>
<details>
<summary><b>4. 회원탈퇴</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE user_withdraw(in delete_email varchar(255))
BEGIN
  update user set del_yn = 'Y' where email = delete_email;
END
// DELIMITER ;
 ```
</details>
</div>
</details>

<details>
<summary><b>📘강좌</b></summary>
<div>
<details>
<summary><b>1. 강좌등록(강사)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE course_upload(in nameInput varchar(255), in descriptionInput varchar(8000), in priceInput decimal(10,2), in categoryInput varchar(255), in start_dateInput datetime, in end_dateInput datetime, in instructor_idInput bigint, in maxInput int )
BEGIN
  insert into course(name, description, price, category, start_date, end_date, instructor_id, max_student) values (nameInput, descriptionInput, priceInput, categoryInput, start_dateInput, end_dateInput, instructor_idInput, maxInput);
END
// DELIMITER ;
```
</details>
<details>
<summary><b>2. 강좌승인(관리자)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE course_approval(in course_idInput bigint)
BEGIN
  update course set approval = 'Y' where id = course_idInput;
 END
 // DELIMITER ;
```
</details>
<details>
<summary><b>3. 강좌수강신청(학생)</b></summary>

```sql
DELIMITER //
create procedure 수강신청 (in 학생id bigint(20),in 강좌id bigint(20))
BEGIN
  insert into course_register (student_id,course_id) values (학생id,강좌id);
END
// DELIMITER ;
```
</details>
<details>
<summary><b>4. 승인강좌전체조회(회원)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE course_all_search()
BEGIN
  select c.name as'강좌명', u.name as'강사명', c.price as'가격', c.max_student as'전체인원' 
  from course c left join user u on c.instructor_id = u.id 
  where c.approval = 'Y';
END
// DELIMITER ;
```
</details>
<details>
<summary><b>5. 승인강좌단일조회(회원-강좌명검색)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE course_one_search(in 강좌명 varchar(255))
BEGIN
  select c.name as '강좌명', u.name as '강사명', c.price as '가격', c.max_student as '전체인원' 
  from course c left join user u on c.instructor_id = u.id 
  where c.approval = 'Y' and c.name = 강좌명;
END
// DELIMITER ;
```
</details>
<details>
<summary><b>6. 수강강좌전체조회(학생)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE register_all_search(in 학생id bigint(20))
BEGIN
  select c.name as 수강강좌명
  from course_register r inner join course c on r.course_id = c.id
  where r.student_id = 학생id; 
END
// DELIMITER ;
```
</details>
<details>
<summary><b>7. 수강강좌단일조회(학생)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE register_one_search(in 학생id bigint(20), in 강좌id bigint(20))
BEGIN
  select c.name as 수강강좌명
  from course_register r inner join course c on r.course_id = c.id
  where r.student_id = 학생id and r.course_id = 강좌id; 
END
// DELIMITER ;
```
</details>
<details>
<summary><b>8. 수강강좌취소(학생)</b></summary>

 ```sql
DELIMITER //
CREATE PROCEDURE register_delete(in 학생id bigint(20), in 강좌명 varchar(255))
BEGIN
declare courseId bigint(20);
  select id into courseId from course where name = 강좌명;
  update course_register set del_yn = 'Y' where student_id = 학생id and course_id = courseId;
END
// DELIMITER ;
```
</details>
<details>
<summary><b>9. 수강강좌전체조회(학생)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE `get_student_courses` (IN studentId BIGINT(20) UNSIGNED)
BEGIN
  SELECT c.*
  FROM course c
  INNER JOIN course_register cr ON c.id = cr.course_id
  WHERE cr.student_id = studentId
  AND cr.del_yn = 'N'
  AND c.del_yn = 'N';
END 
// DELIMITER ;
```
</details>
</div>
</details>

<details>
<summary><b>📖강의</b></summary>
<div>
<details>
<summary><b>1. 강의등록(강사)</b></summary>

```sql
DELIMITER //
CREATE PROCEDURE lecture_upload(in instructorEmail varchar(255), in courseId bigint, in name varchar(255), in content varchar(255), in running_time Time)
BEGIN
    declare courseId bigint;        -- course_id
    declare instructorId bigint;        -- instructor_id
    select id into instructorId from user where email = instructorEmail;

    select id into courseId from course where id = courseIdInput and instructor_id =instructorId;
    
    if courseId is null then
      select '해당 강좌가 존재하지 않습니다.';
    else
      insert into lecture (name, content, course_id, running_time) values (name, content, courseId, running_time);
      select '강의 생성 완료';
    end if;
END
// DELIMITER ;
```
</details>
<details>
<summary><b>2. 강의삭제(강사)</b></summary>

```sql
DELIMITER //
CREATE DEFINER=`root`@`localhost` PROCEDURE `lecture_delete`(in instructorEmail varchar(255), in courseId bigint, in lectureId bigint)
BEGIN
    declare instructorId bigint;
    declare deleteCourseId bigint;
    declare deleteLectureName varchar(255);
    declare deleteLectureId bigint;
    select id into instructorId from user where email = instructorEmail;
    select id into deleteCourseId from course where id = courseId and instructor_id= instructorId;
    if deleteCourseId is null then
      select '해당 강좌가 존재하지 않습니다.';
    else
      select id, name into deleteLectureId, deleteLectureName from lecture where id= lectureId;
    if deleteLectureId is null then
      select '해당 강의가 존재하지 않습니다.';
    else
      update lecture set del_yn = 'Y' where id = deleteLectureId;
      select concat(deleteLectureName, '강의 삭제') ;
    end if;
    end if;
END
// DELIMITER ;
```
</details>
<details>
<summary><b>3. 강의단일조회(회원)</b></summary>

```sql
DELIMITER //
CREATE DEFINER=`root`@`localhost` PROCEDURE `lecture_one_search`(in courseId bigint, in lectureId bigint)
BEGIN
    select name as '강의명', content as '동영상', running_time as '강의 시간', created_date as '강의 생성일' from lecture where course_id = courseId and del_yn = 'N' and id = lectureId;
END
// DELIMITER ;
```
</details>
<details>
<summary><b>4. 강의전체조회(회원)</b></summary>

```sql
DELIMITER //
CREATE DEFINER=`root`@`localhost` PROCEDURE `lecture_total_search`(in courseId bigint)
BEGIN
    select name as '강의명', content as '동영상', running_time as '강의 시간', created_date as '강의 생성일' from lecture where course_id = courseId and del_yn = 'N';
END
// DELIMITER ;
```
</details>
<details>
<summary><b>5. 강의시청(학생)</b></summary>

```sql
DELIMITER //
CREATE DEFINER=`root`@`localhost` PROCEDURE `lecture_watch`(in studentEmail varchar(255), in lectureId bigint)
BEGIN
declare studentId bigint;
    declare registerId bigint default null;
    declare attendanceId bigint default null;-- 강의 시청 이력
    
    -- 학생의 id
    select id into studentId from user where email = studentEmail;
 
    -- 강좌를 수강하고 있는지. 하고 있으면 registerId에 course_register의 pk인 id가 들어감. 아니면 null
    select cr.id into registerId from course_register cr inner join lecture l on l.course_id = cr.course_id where cr.student_id = studentId and l.id = lectureId and l.del_yn = 'N';

    if registerId is null then
select '해당 강좌를 수강하고 있지 않습니다.';
else 
select id into attendanceId from attendance where student_id = studentId and lecture_id = lectureId;
if attendanceId is null then
select '강의 시청하기';
            insert into attendance (student_id, lecture_id) values (studentId, lectureId);
        else
select '강의 재시청';
        end if;
end if; 
END
// DELIMITER ;
```
</details>

<details>
<summary><b>6. 출결확인</b></summary>

```sql
DELIMITER //
CREATE DEFINER=`root`@`localhost` PROCEDURE `attendance_total_search`(in studentEmail varchar(255))
BEGIN
declare studentId bigint;
    select id into studentId from user where email = studentEmail;
    
    select c.name as '강의명', count(a.id) as '시청한 강의 수', count(*) as '전체 강의 수'
from course_register cr  right outer join lecture l on cr.course_id = l.course_id 
inner join course c on c.id = cr.course_id 
left outer join attendance a on l.id = a.lecture_id  and a.student_id = studentId
where l.del_yn = 'N' and cr.student_id = studentId
group by cr.course_id;
END
// DELIMITER ;

```
</details>

</div>
</details>

<hr>

### 🧪 테스트 케이스

#### 👨‍💻 강사
<details>
<summary><b>강좌 등록 신청</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/course_upload.png">
</details>
<details>
<summary><b>강좌 개설 신청된 강좌 승인</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/course_approval.png">
</details>
<details>
<summary><b>전체 강좌 조회</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/course_all_select.png">
</details>
<details>
<summary><b>강좌 검색</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/course_search.png">
</details>
<details>
<summary><b>강의 생성</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/lecture_create.png">
</details>
<details>
<summary><b>한 강좌에 대한 강의 전체 조회</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/total_search.png">
</details>
<details>
<summary><b>강좌에 대한 질문 대답하기</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/question.png">
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/response.png">
</details>
<details>
<summary><b>과제 등록 및 조회</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/work_upload_select.png">
</details>


#### 👩‍💻 학생
<details>
<summary><b>회원 회원가입</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/join.png">
</details>
<details>
<summary><b>전체 강좌 조회</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/user_course_select.png">
</details>
<details>
<summary><b>수강 신청 하기</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/register.png">
</details>
<details>
<summary><b>결제 할 카드 등록</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/card_upload.png">
</details>
<details>
<summary><b>수강하는 전체 강좌를 조회</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/register_all_select.png">
</details>
<details>
<summary><b>수강하는 강좌 취소</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/register_delete.png">
</details>
<details>
<summary><b>질문 게시글 등록</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/question_1.png">
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/question_2.png">
</details>
<details>
<summary><b>질문에 대한 답변 조회</b></summary>
<img src="https://github.com/beyond-sw-camp/be07-1st-6team-classdom/blob/main/classdom/image/response_select.png">
</details>
<hr>



