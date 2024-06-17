<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Compras</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        h1 {
            margin-bottom: 20px;
        }
        input[type="text"] {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            width: calc(100% - 22px); /* Ajusta a largura para incluir padding e borda */
        }
        button {
            padding: 10px;
            background-color: #28a745;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 10px;
            width: 100%;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            background-color: #f9f9f9;
            margin-bottom: 5px;
            border-radius: 4px;
        }
        li.checked {
            text-decoration: line-through;
            color: #aaa;
        }
        li button {
            background-color: #dc3545;
            border: none;
            color: white;
            border-radius: 4px;
            padding: 5px 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Lista de Compras</h1>
        <input type="text" id="itemInput" placeholder="Adicionar item..." />
        <button onclick="addItem()">Adicionar</button>
        <ul id="itemList"></ul>
    </div>

    <script>
        function addItem() {
            const input = document.getElementById('itemInput');
            const itemText = input.value.trim();
            
            if (itemText !== '') {
                const ul = document.getElementById('itemList');
                const li = document.createElement('li');

                li.innerHTML = `${itemText} <button onclick="removeItem(this)">Remover</button>`;
                li.addEventListener('click', function() {
                    this.classList.toggle('checked');
                });

                ul.appendChild(li);
                input.value = '';
            }
        }

        function removeItem(button) {
            const li = button.parentNode;
            li.parentNode.removeChild(li);
        }

        document.getElementById('itemInput').addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                addItem();
            }
        });
    </script>
</body>
</html>
