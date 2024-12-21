<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instituto Politécnico do Maiombe - IPM 4024</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            transition: background-color 0.5s ease;
        }
        header {
            background-color: #0044cc;
            color: #fff;
            padding: 1rem 0;
            text-align: center;
        }
        nav {
            background-color: #003399;
            color: #fff;
            padding: 0.5rem 0;
            text-align: center;
        }
        nav a {
            color: #fff;
            margin: 0 1rem;
            text-decoration: none;
        }
        nav a:hover {
            text-decoration: underline;
        }
        main {
            padding: 2rem;
            text-align: center;
        }
        section {
            margin-bottom: 2rem;
        }
        footer {
            background-color: #0044cc;
            color: #fff;
            padding: 1rem 0;
            position: fixed;
            bottom: 0;
            width: 100%;
            text-align: center;
        }
        .modo-escuro {
            background-color: #2e2e2e;
            color: #ddd;
        }
        .modo-escuro header,
        .modo-escuro nav,
        .modo-escuro footer {
            background-color: #1a1a1a;
        }
        .modo-escuro nav a {
            color: #bbb;
        }
        #galeria img {
            width: 200px;
            height: auto;
            margin: 10px;
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        #galeria img:hover {
            transform: scale(1.1);
        }
    </style>
    <script>
        const database = {
            alunos: [],
            notas: [],
            documentos: []
        };

        function adicionarAluno(nome, matricula) {
            database.alunos.push({ nome, matricula });
            alert(`Aluno ${nome} adicionado com sucesso!`);
        }

        function registrarNota(matricula, nota) {
            database.notas.push({ matricula, nota });
            alert(`Nota registrada para o aluno com matrícula ${matricula}.`);
        }

        function enviarDocumento(matricula, documento) {
            database.documentos.push({ matricula, documento });
            alert(`Documento enviado para o aluno com matrícula ${matricula}.`);
        }

        function verificarLogin() {
            const senhaCorreta = "senhaSegura";
            const senha = prompt("Digite a senha de administrador:");

            if (senha === senhaCorreta) {
                alert("Acesso concedido.");
            } else {
                alert("Acesso negado. Senha incorreta.");
                throw new Error("Acesso negado.");
            }
        }

        function alternarModoEscuro() {
            document.body.classList.toggle('modo-escuro');
        }

        function mostrarContadorVisitantes() {
            let contador = localStorage.getItem('contadorVisitas') || 0;
            contador = parseInt(contador) + 1;
            localStorage.setItem('contadorVisitas', contador);
            document.getElementById('contador-visitantes').textContent = `Visitantes: ${contador}`;
        }

        window.addEventListener('load', mostrarContadorVisitantes);
    </script>
</head>
<body>
    <header>
        <h1>Bem-vindo ao Instituto Politécnico do Maiombe - IPM 4024</h1>
        <button onclick="alternarModoEscuro()">Alternar Modo Escuro</button>
    </header>
    <nav>
        <a href="#sobre">Sobre Nós</a>
        <a href="#cursos">Cursos</a>
        <a href="#eventos">Eventos</a>
        <a href="#contato">Contato</a>
        <a href="#galeria">Galeria</a>
    </nav>
    <main>
        <section id="sobre">
            <h2>Sobre o Instituto</h2>
            <p>O Instituto Politécnico do Maiombe (IPM 4024) é referência em educação técnica e profissional, comprometido com a formação de excelência para nossos alunos.</p>
        </section>
        <section id="cursos">
            <h2>Cursos Disponíveis</h2>
            <p>Oferecemos uma ampla variedade de cursos técnicos e profissionais nas áreas de engenharia, tecnologia e ciências aplicadas.</p>
        </section>
        <section id="eventos">
            <h2>Próximos Eventos</h2>
            <p>Acompanhe nossos eventos acadêmicos, palestras e feiras educacionais.</p>
        </section>
        <section id="administracao">
            <h2>Administração</h2>
            <button onclick="verificarLogin(); adicionarAluno(prompt('Nome do aluno:'), prompt('Matrícula do aluno:'))">Adicionar Aluno</button>
            <button onclick="verificarLogin(); registrarNota(prompt('Matrícula do aluno:'), prompt('Nota:'))">Registrar Nota</button>
            <button onclick="verificarLogin(); enviarDocumento(prompt('Matrícula do aluno:'), prompt('Descrição do documento:'))">Enviar Documento</button>
        </section>
        <section id="contato">
            <h2>Fale Conosco</h2>
            <p>Email: <a href="mailto:contato@ipm4024.com">contato@ipm4024.com</a></p>
            <p>Telefone: (11) 1234-5678</p>
        </section>
        <section id="galeria">
            <h2>Galeria de Fotos</h2>
            <div>
                <img src="https://via.placeholder.com/200" alt="Foto 1">
                <img src="https://via.placeholder.com/200" alt="Foto 2">
                <img src="https://via.placeholder.com/200" alt="Foto 3">
            </div>
        </section>
        <section id="visitantes">
            <h2>Contador de Visitantes</h2>
            <p id="contador-visitantes">Visitantes: 0</p>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Instituto Politécnico do Maiombe - IPM 4024. Todos os direitos reservados.</p>
    </footer>
</body>
</html>
