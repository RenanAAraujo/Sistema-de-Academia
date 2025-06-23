# Sistema de Academia

Este projeto é um sistema web para gerenciamento de academia, construído em **PHP** (sem framework), utilizando **Bootstrap 5** (template DarkPan) e **MySQL/MariaDB** como banco de dados.

---

## Índice

1. [Pré-requisitos](#pré-requisitos)
2. [Instalação](#instalação)
3. [Importação do Banco de Dados](#importação-do-banco-de-dados)
4. [Configuração](#configuração)
5. [Estrutura de Pastas](#estrutura-de-pastas)
6. [Funcionalidades Principais](#funcionalidades-principais)
7. [Usuários & Autenticação](#usuários--autenticação)
8. [Relatórios](#relatórios)
9. [Melhorias Sugeridas](#melhorias-sugeridas)
10. [Contribuição](#contribuição)
11. [Licença](#licença)

---

## Pré-requisitos

- **PHP** 7.4+ com suporte a extensões PDO e mysqli
- **MySQL** ou **MariaDB** 10+ (servidor local ou remoto)
- Servidor web (Apache ou Nginx)
- Composer (opcional, se adicionar dependências)

---

## Instalação

1. Faça o download ou clone este repositório:
   ```bash
   git clone https://seu-repositorio.com/Sistema-de-Academia-main.git
   cd Sistema-de-Academia-main
   ```
2. Copie o arquivo de configuração de exemplo (se houver) e edite com suas credenciais:
   ```bash
   cp config.sample.php config.php
   ```
3. Configure o servidor web apontando o **DocumentRoot** para o diretório raiz do projeto.
4. Certifique-se de que o `.htaccess` está habilitado (mod\_rewrite no Apache).

---

## Importação do Banco de Dados

1. Crie um banco de dados vazio, por exemplo `academia`.
2. Importe o arquivo SQL com esquema e dados de exemplo:
   ```bash
   mysql -u usuario -p academia < academia.sql
   ```
3. Verifique se as tabelas foram criadas (`alunos`, `exercicios`, `fichas`, `eventos`, `administradores`, etc.).

---

## Configuração

- **config.php**: arquivo de conexão ao banco de dados. Exemplo:
  ```php
  <?php
  define('DB_HOST', 'localhost');
  define('DB_NAME', 'academia');
  define('DB_USER', 'root');
  define('DB_PASS', 'senha');
  try {
      $pdo = new PDO("mysql:host=".DB_HOST.";dbname=".DB_NAME, DB_USER, DB_PASS);
      $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
  } catch (PDOException $e) {
      die("Erro ao conectar: " . $e->getMessage());
  }
  ```
- **.htaccess**: regras de reescrita de URL e restrições de acesso. Ajuste conforme seu ambiente.

---

## Estrutura de Pastas

```
Sistema-de-Academia-main/
├─ .htaccess                    # Regras de URL e segurança
├─ academia.sql                 # Dump do banco com esquema e dados de exemplo
├─ config.sample.php            # Exemplo de configuração do DB
├─ index.html                   # Landing page
│
├─ admin/                       # Painel administrativo
│   ├─ home_adm.php             # Dashboard
│   ├─ perfil.php               # Edição de perfil
│   ├─ administrador.php        # CRUD de administradores
│   ├─ cadastro_aluno.php       # Criar aluno
│   ├─ editar_aluno.php         # Editar aluno
│   ├─ deletar_aluno.php        # Excluir aluno
│   ├─ cadastrar_exercicio.php  # Criar exercício
│   ├─ lista_exercicios.php     # Listar exercícios
│   ├─ eventos_adm.php          # Gerenciar eventos
│   └─ exportar_relatorio.php   # Geração de relatórios CSV/PDF
│
├─ usuarios/                    # Área do aluno
│   ├─ ficha_do_usuario.php     # Visualizar ficha de treino
│   ├─ eventos_usuario.php      # Lista de eventos disponíveis
│   └─ include/                 # Includes comuns (header, footer, conexão)
│       ├─ conexao.php
│       ├─ header_usuario.php
│       └─ footer.php
│
├─ scss/                        # Código-fonte SCSS do Bootstrap 5
├─ css/                         # CSS compilado (Bootstrap + adicionais)
├─ js/                          # Scripts front-end (main.js)
└─ lib/                         # Plugins de terceiros (Chart.js, OwlCarousel, etc.)
```

---

## Funcionalidades Principais

- **CRUD Completo**: gerencie alunos, exercícios, fichas e eventos
- **Dashboard**: gráficos e estatísticas de participação (Chart.js)
- **Agenda de Eventos**: agendamento e visualização de eventos para alunos
- **Fichas de Treino**: criação e consulta de planos de treino personalizados
- **Relatórios**: exportação de dados em CSV ou PDF para análise

---

## Usuários & Autenticação

- **Administrador**: acesso completo ao painel `administrador/`, sessão PHP e logout.
- **Aluno**: acesso à própria ficha e eventos em `usuários/`.

> **Credenciais iniciais** (exemplo):
>
> - Usuário: `admin@academia.com` /Senha: `administrador123`
> - Aluno de exemplo: `aluno1@academia.com` /Senha: `aluno123`

---

## Relatórios

- Uma opção **Exportar Relatório** gera arquivos **CSV** ou **PDF** contendo dados de alunos, fichas ou eventos.
- Personalize o modelo de PDF em `admin/exportar_relatorio.php` usando **Dompdf** ou **TCPDF**.

---

## Melorias Sugeridas

1. **Segurança**:

   - Usar **declarações preparadas** (DOP) para todas como consultas.
   - Proteger formulários com tokens CSRF.
   - Hashear senhas (bcrypt) em vez de texto puro.

2. **Construir Front-End**:

   - Adotar **Vite** ou **Webpack** para compilar SCSS e JS.
   - Ativos Otimizar (imagem, CSS e scripts).

3. **Arquitetura**:

   - Migrar para um framework MVC (Laravel, Symfony) para melhor organização.
   - Implementar roteamento centralizado e middlewares.

4. **Testes e CI/CD**:

   - Escrever testes unitários e funcionais (PHPUnit, Selenium).
   - Pipeline Configurar de CI (Ações GitHub, GitLab CI).

---

## Contribuição

Contribuições são bem-vindas:

1. Fork este projeto
2. Filial Crie Uma: `git checkout - b feature/nome-da-feature`
3. Comprometer-se: `git commit - m "Descrição da feature"`
4. Empurrar: `recurso de origem git push/nome-da-feature`
5. Abra um Pull Solicitação

---

## Licença

Este projeto utiliza o template DarkPan sob **Licença MIT**. . Consulte `LICENÇA.txt` para detalhes.

