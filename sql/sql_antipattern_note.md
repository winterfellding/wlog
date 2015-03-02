1. Jaywalking
    use string seprate with comma instead of using an intersection table on many-to-many relationship.
    1.使用后where fk=？不好用了
    2.count sum这些函数不能使用了
    3.update加新id很复杂
    4.无法确定是正确的
    5.会有最大长度限制，可能超过
    解决方案：使用intersection table

2. Naive trees

    CREATE TABLE Comments (
        comment_id SERIAL PRIMARY KEY,
        parent_id BIGINT UNSIGNED,
        bug_id BIGINT UNSIGNED NOT NULL,
        author BIGINT UNSIGNED NOT NULL,
        comment_date DATETIME NOT NULL,
        comment TEXT NOT NULL,
        FOREIGN KEY (parent_id) REFERENCES Comments(comment_id),
        FOREIGN KEY (bug_id) REFERENCES Bugs(bug_id),
        FOREIGN KEY (author) REFERENCES Accounts(account_id)
    );
    Adjacency list
    1.不能把所有层次取出来，使用join只能取出两个层次的comment
    2.很难计算集合问题中的count sum之类的东西
    3.要么都取出来之后在app中构建tree数据结构，但全取出来的话可能是个巨大的数据量
    4.加一个叶子很容易，但删除一个子树很复杂
