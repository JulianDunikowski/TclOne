CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100) UNIQUE NOT NULL
);

CREATE TABLE posts (
    id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(id),
    title VARCHAR(100),
    content TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');
INSERT INTO posts (user_id, title, content) VALUES (1, 'My First Post', 'This is my first blog post!');

SELECT users.name, posts.title, posts.content 
FROM posts JOIN users ON posts.user_id = users.id;
