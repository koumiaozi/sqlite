1.select name from book, member, checkout_item where book_id=book.id and member_id=member.id and title='The Hobbit';

Anand Beck

2.select count(member.id) from member where member.id not in (select distinct(member_id) from checkout_item where book_id  not null);

39

3.select id from book where id not in (select distinct(book_id) from checkout_item where book_id not null); 

Books:2,6,7,8,9,10

sqlite> select id from movie where id not in (select distinct(movie_id) from checkout_item where movie_id not null);

Movies:6,7,8,9

4.insert into book(title) values("The Pragmatic Programmer");

 insert into member(name) values("Kou Miaojuan");

insert into checkout_item(member_id,book_id) values("43","11");

select name from book, member, checkout_item where book_id=book.id and member_id=member.id and title='The Pragmatic Programmer';

5.select name from member where id in (select member_id from (select member_id, count(book_id) as book_numbers, count(movie_id) as movie_numbers from checkout_item  group by member_id) as temp where book_numbers + movie_numbers >1);

Anand Beck
Frank Smit



