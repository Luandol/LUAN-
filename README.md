<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biblioteca</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Biblioteca</h1>
        <form id="book-form">
            <input type="text" id="title" placeholder="Título do Livro" required>
            <input type="text" id="author" placeholder="Autor do Livro" required>
            <button type="submit">Adicionar Livro</button>
        </form>
        <h2>Lista de Livros</h2>
        <ul id="book-list"></ul>
    </div>
    <script src="scripts.js"></script>
</body>
</html>body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
}

.container {
    width: 80%;
    margin: auto;
    overflow: hidden;
}

h1, h2 {
    text-align: center;
}

form {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

input[type="text"] {
    padding: 10px;
    margin-right: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

button {
    padding: 10px 20px;
    border: none;
    background-color: #333;
    color: #fff;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #555;
}

ul {
    list-style: none;
    padding: 0;
}

ul li {
    background: #fff;
    margin: 10px 0;
    padding: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

ul li button {
    background: red;
    border: none;
    color: #fff;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
}

ul li button:hover {
    background: darkred;
}document.getElementById('book-form').addEventListener('submit', function (e) {
    e.preventDefault();

    const title = document.getElementById('title').value;
    const author = document.getElementById('author').value;

    if (title !== '' && author !== '') {
        const li = document.createElement('li');
        li.appendChild(document.createTextNode(`${title} por ${author}`));

        const deleteBtn = document.createElement('button');
        deleteBtn.appendChild(document.createTextNode('Remover'));
        li.appendChild(deleteBtn);

        document.getElementById('book-list').appendChild(li);

        deleteBtn.addEventListener('click', function () {
            document.getElementById('book-list').removeChild(li);
        });

        document.getElementById('book-form').reset();
    }
});
