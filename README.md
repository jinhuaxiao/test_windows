# hello mysql  
## mysql merge 引擎测试代码 
create table if not exists user1(
id int(11) not null auto_increment,
name varchar(50) default null,
sex int(1) not null default 0,
primary key (id)
) engine=Myisam default charset=utf8 auto_increment=1;

create table if not exists user2(
id int(11) not null auto_increment,
name varchar(50) default null,
sex int(1) not null default 0,
primary key (id)
) engine=Myisam default charset=utf8 auto_increment=1;

create table if not exists alluser (
	id int(11) not null auto_increment,
	name varchar(50) default null,
	sex int(1) not null default 0,
	index(id)
)engine=merge union=(user1,user2) insert_method=last auto_increment=1;

insert into user1 (name,sex) values ('张延',0);
insert into user2 (name,sex) values ('tank',0);
insert into alluser (name,sex) values ('alluser',0);
