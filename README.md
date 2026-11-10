# 🧠 Sistema Musical — FASE 2: Backend Completo (PHP + MySQL)

Este repositório contém a aplicação completa do **Sistema Musical**, desenvolvida em PHP e MySQL com integração à interface em HTML5 e CSS3.

O sistema possui autenticação de utilizadores com palavra-passe encriptada, gestão de sessões, CRUD completo de artistas e músicas, redimensionamento automático de fotos/capas de álbuns via extensão GD e biblioteca musical interativa com filtros dinâmicos.

---

## 📌 Sobre o Projeto

O **Sistema Musical** permite a gestão centralizada de catálogos musicais. Na Fase 2, todas as páginas estáticas foram convertidas em scripts PHP dinâmicos e ligadas à base de dados MySQL `sistema_musical_v2`.

---

## 🚀 Funcionalidades do Backend

- 🔒 **Autenticação e Segurança:**
  - Login seguro com validação de palavras-passe via `password_verify()` (algoritmo Bcrypt).
  - Proteção de páginas restritas com controlo de sessão (`valida_sessao.php`).
  - Prevenção contra ataques SQL Injection através de *Prepared Statements* (`mysqli::prepare`).
  - Proteção contra XSS via higienização de saída (`htmlspecialchars`).
  - Função de logout seguro com destruição de cookies e sessão no servidor.

- 🎤 **Gestão de Artistas (`cadastro_artista.php`):**
  - CRUD completo (Criar, Ler, Atualizar, Apagar).
  - Redimensionamento automático de fotos enviadas (JPG/PNG até 5 MB para 300x300px via extensão PHP GD).
  - Validação de integridade referencial (impede a exclusão de artistas que possuam músicas associadas).

- 🎵 **Gestão de Músicas (`cadastro_musica.php`):**
  - Associação de faixas a artistas por chave estrangeira (`artista_id`).
  - Extração automática de ID de vídeos do YouTube a partir de múltiplos formatos de URL (Watch, Embed, Short URLs).
  - Upload e redimensionamento de capas de álbuns.
  - Eliminação automática dos ficheiros físicos de imagem do servidor ao apagar registos (`unlink`).

- 🎼 **Biblioteca Musical (`listagem_musicas.php`):**
  - Filtros combinados via formulário GET (pesquisa por título/álbum/artista, filtro por artista e por género).
  - Links diretos para reprodução externa de vídeos no YouTube (`target="_blank"` com `rel="noopener noreferrer"`).
  - Preservação dos parâmetros de pesquisa ativos na URL após ações de exclusão.

---

## 📁 Estrutura do Projeto

```text
sistema-musical/
├── styles.css               # Folha de estilos centralizada e responsiva
├── bd.sql                   # Script SQL de criação e povoamento da base de dados
├── conexao.php              # Script de ligação ao MySQL e criação da pasta de uploads
├── geraSenha.php            # Utilitário de linha de comando para gerar hash Bcrypt
├── valida_sessao.php        # Middleware de validação de sessão ativa
├── login.php                # Autenticação de utilizadores
├── logout.php               # Encerramento seguro de sessão
├── index.php                # Painel de navegação principal (Menu)
├── cadastro_artista.php     # CRUD de artistas com upload de imagem
├── cadastro_musica.php      # CRUD de músicas com suporte a YouTube e capas
├── listagem_musicas.php     # Biblioteca musical com filtros dinâmicos
└── img/                     # Diretório de armazenamento de imagens (criado automaticamente)
