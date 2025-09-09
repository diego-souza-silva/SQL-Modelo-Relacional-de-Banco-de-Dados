# SQLite online - conhecendo instruções SQL.
Aprendi a criar e estruturar tabelas com chaves primárias e estrangeiras, inserir, consultar, atualizar e excluir dados, mantendo a integridade da base. Desenvolvi um modelo relacional completo com alunos, professores, disciplinas e notas, realizando consultas para análise de informações.


CREATE TABLE ALUNOS 
( ID_ALUNO INT PRIMARY KEY,
 NOME_DO_ALUNO VARCHAR (100),
 DATA_DE_NASCIMENTO DATE,
 GENERO VARCHAR (20),
 ENDEREÇO VARCHAR (150),
 TELEFONE_DE_CONTATO VARCHAR (20),
 EMAIL VARCHAR (250));
 
 CREATE TABLE PROFESSORES
( ID_PROFESSOR INT PRIMARY KEY,
 NOME_DO_PROFESSOR VARCHAR (100),
 DATA_DE_NASCIMENTO DATE,
 GENERO VARCHAR (20),
 TELEFONE_DE_CONTATO VARCHAR (20),
 EMAIL VARCHAR (250));
 
  CREATE TABLE DISCIPLINAS
 ( ID_DISCIPLINA INT PRIMARY KEY,
  NOME_DA_DISCIPLINA VARCHAR (100),
  DESCRICAO VARCHAR (250),
  CARGA_HORARIA DECIMAL (10.2),
  ID_PROFESSOR INT,
  FOREIGN KEY (ID_PROFESSOR) REFERENCES PROFESSORES(ID_PROFESSOR));
  
 CREATE TABLE TURMAS
( ID_TURMA INT PRIMARY KEY,
 NOME_DA_TURMA VARCHAR (100),
 ANO_LETIVO INT,
 ID_PROFESSOR_ORIENTADOR INT,
 FOREIGN KEY (ID_PROFESSOR_ORIENTADOR) REFERENCES PROFESSORES(id_professor));
 
 
  CREATE TABLE TURMAS_DISCIPLINAS
( ID_TURMA INT,
  ID_DISCIPLINAS INT,
 FOREIGN KEY (ID_TURMA) REFERENCES TURMAS(id_turma),
 FOREIGN KEY (ID_DISCIPLINAS) REFERENCES DISCIPLINAS (id_disciplina));
 
 
 CREATE TABLE TURMAS_ALUNOS
( ID_TURMA INT,
  ID_ALUNO INT,
  PRIMARY KEY (ID_TURMA, ID_ALUNO),
  FOREIGN KEY (ID_TURMA) REFERENCES TURMAS(ID_TURMA),
  FOREIGN KEY (ID_ALUNO) REFERENCES ALUNOS(ID_ALUNO));
  
CREATE TABLE NOTAS
( ID_NOTAS INT PRIMARY KEY,
  ID_ALUNO INT,
  ID_DISCIPLINA INT,
  VALOR_DA_NOTA DECIMAL (10,2),
  DATA_DA_AVALIACAO DATE,
  FOREIGN KEY (ID_ALUNO) REFERENCES ALUNOS(ID_ALUNO),
  FOREIGN KEY (ID_DISCIPLINA) REFERENCES DISCIPLINAS (id_disciplina));
 

 
INSERT INTO ALUNOS
( ID_ALUNO,
 NOME_DO_ALUNO,
 DATA_DE_NASCIMENTO,
 GENERO,
 ENDEREÇO,
 TELEFONE_DE_CONTATO,
 EMAIL)
 
 VALUES
(1, 'João Silva', '2005-03-15', 'Masculino', 'Rua das Flores, 123', '(11) 9876-5432', 'joao@email.com'),
(2, 'Maria Santos', '2006-06-20', 'Feminino', 'Avenida Principal, 456', '(11) 8765-4321', 'maria@email.com'),
(3, 'Pedro Soares', '2004-01-10', 'Masculino', 'Rua Central, 789', '(11) 7654-3210', 'pedro@email.com'),
(4, 'Ana Lima', '2005-04-02', 'Feminino', 'Rua da Escola, 56', '(11) 8765-4321', 'ana@email.com'),
(5, 'Mariana Fernandes', '2005-08-12', 'Feminino', 'Avenida da Paz, 789', '(11) 5678-1234', 'mariana@email.com'),
(6, 'Lucas Costa', '2003-11-25', 'Masculino', 'Rua Principal, 456', '(11) 1234-5678', 'lucas@email.com'),
(7, 'Isabela Santos', '2006-09-10', 'Feminino', 'Rua da Amizade, 789', '(11) 9876-5432', 'isabela@email.com'),
(8, 'Gustavo Pereira', '2004-05-15', 'Masculino', 'Avenida dos Sonhos, 123', '(11) 7654-3210', 'gustavo@email.com'),
(9, 'Carolina Oliveira', '2005-02-20', 'Feminino', 'Rua da Alegria, 456', '(11) 8765-4321', 'carolina@email.com'),
(10, 'Daniel Silva', '2003-10-05', 'Masculino', 'Avenida Central, 789', '(11) 1234-5678', 'daniel@email.com'),
(11, 'Larissa Souza', '2004-12-08', 'Feminino', 'Rua da Felicidade, 123', '(11) 9876-5432', 'larissa@email.com'),
(12, 'Bruno Costa', '2005-07-30', 'Masculino', 'Avenida Principal, 456', '(11) 7654-3210', 'bruno@email.com'),
(13, 'Camila Rodrigues', '2006-03-22', 'Feminino', 'Rua das Estrelas, 789', '(11) 8765-4321', 'camila@email.com'),
(14, 'Rafael Fernandes', '2004-11-18', 'Masculino', 'Avenida dos Sonhos, 123', '(11) 1234-5678', 'rafael@email.com'),
(15, 'Letícia Oliveira', '2005-01-05', 'Feminino', 'Rua da Alegria, 456', '(11) 9876-5432', 'leticia@email.com'),
(16, 'Fernanda Lima', '2004-02-12', 'Feminino', 'Rua da Esperança, 789', '(11) 4567-8901', 'fernanda@email.com'),
(17, 'Vinícius Santos', '2003-07-28', 'Masculino', 'Avenida da Amizade, 123', '(11) 8901-2345', 'vinicius@email.com'),
(18, 'Juliana Pereira', '2006-09-01', 'Feminino', 'Rua das Rosas, 789', '(11) 3456-7890', 'juliana@email.com');

INSERT INTO DISCIPLINAS
( ID_DISCIPLINA,
  NOME_DA_DISCIPLINA,
  DESCRICAO,
  CARGA_HORARIA,
  ID_PROFESSOR)
  
  VALUES
(1, 'Matemática', 'Estudo de conceitos matemáticos avançados', 60, 1),
(2, 'História', 'História mundial e local', 45, 2),
(3, 'Física', 'Princípios fundamentais da física', 60, 1),
(4, 'Química', 'Estudo da química e suas aplicações', 45, 3),
(5, 'Inglês', 'Aulas de inglês para iniciantes', 45, 4),
(6, 'Artes', 'Exploração da criatividade artística', 30, 5);


INSERT INTO NOTAS
( ID_NOTAS,
  ID_ALUNO,
  ID_DISCIPLINA,
  VALOR_DA_NOTA,
  DATA_DA_AVALIACAO)
  
  VALUES
(2, 1, 1, 6.19, '2023-07-07'),
(3, 1, 2, 7.18, '2023-07-07'),
(4, 1, 3, 7.47, '2023-07-07'),
(5, 1, 4, 7.46, '2023-07-07'),
(6, 1, 5, 4.35, '2023-07-07'),
(7, 1, 6, 4.43, '2023-07-07'),
(8, 1, 7, 0.76, '2023-07-07'),
(9, 1, 8, 9.22, '2023-07-07'),
(10, 1, 9, 9.04, '2023-07-07'),
(11, 1, 10, 3.28, '2023-07-07'),
(12, 2, 1, 1.34, '2023-07-09'),
(13, 2, 2, 3.10, '2023-07-09'),
(14, 2, 3, 1.66, '2023-07-09'),
(15, 2, 4, 0.03, '2023-07-09'),
(16, 2, 5, 4.34, '2023-07-09'),
(17, 2, 6, 4.02, '2023-07-09'),
(18, 2, 7, 8.79, '2023-07-09'),
(19, 2, 8, 1.17, '2023-07-09'),
(20, 2, 9, 8.26, '2023-07-09'),
(21, 2, 10, 3.41, '2023-07-09'),
(22, 3, 1, 6.82, '2023-07-27'),
(23, 3, 2, 8.21, '2023-07-27'),
(24, 3, 3, 1.30, '2023-07-27'),
(25, 3, 4, 4.01, '2023-07-27'),
(26, 3, 5, 0.25, '2023-07-27'),
(27, 3, 6, 6.63, '2023-07-27'),
(28, 3, 7, 9.74, '2023-07-27'),
(29, 3, 8, 3.77, '2023-07-27'),
(30, 3, 9, 0.58, '2023-07-27'),
(31, 3, 10, 8.52, '2023-07-27'),
(32, 4, 1, 8.37, '2023-08-08'),
(33, 4, 2, 0.26, '2023-08-08'),
(34, 4, 3, 5.95, '2023-08-08'),
(35, 4, 4, 6.98, '2023-08-08'),
(36, 4, 5, 6.18, '2023-08-08'),
(37, 4, 6, 4.79, '2023-08-08'),
(38, 4, 7, 7.96, '2023-08-08'),
(39, 4, 8, 0.62, '2023-08-08'),
(40, 4, 9, 7.77, '2023-08-08'),
(41, 4, 10, 5.81, '2023-08-08'),
(42, 5, 1, 2.25, '2023-08-15'),
(43, 5, 2, 5.82, '2023-08-15'),
(44, 5, 3, 4.11, '2023-08-15'),
(45, 5, 4, 7.99, '2023-08-15'),
(46, 5, 5, 3.23, '2023-08-15'),
(47, 5, 6, 8.09, '2023-08-15'),
(48, 5, 7, 8.24, '2023-08-15'),
(49, 5, 8, 3.33, '2023-08-15'),
(50, 5, 9, 4.24, '2023-08-15'),
(51, 5, 10, 0.11, '2023-08-15');


INSERT INTO PROFESSORES
(ID_PROFESSOR,
 NOME_DO_PROFESSOR,
 DATA_DE_NASCIMENTO,
 GENERO,
 TELEFONE_DE_CONTATO,
 EMAIL)
 
VALUES
(1, 'Ana Oliveira', '1980-05-25', 'Feminino', '(11) 1234-5678', 'ana@email.com'),
(2, 'Carlos Ferreira', '1975-09-12', 'Masculino', '(11) 2345-6789', 'carlos@email.com'),
(3, 'Mariana Santos', '1982-03-15', 'Feminino', '(11) 3456-7890', 'mariana@email.com'),
(4, 'Ricardo Silva', '1978-08-20', 'Masculino', '(11) 7890-1234', 'ricardo@email.com'),
(5, 'Fernanda Lima', '1985-01-30', 'Feminino', '(11) 4567-8901', 'fernanda@email.com');


INSERT INTO TURMAS_ALUNOS 
(ID_TURMA,
 ID_ALUNO)
 
 VALUES
 (1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5),
(1, 6),
(2, 7),
(3, 8),
(4, 9),
(5, 10);


INSERT INTO TURMAS_DISCIPLINAS
(ID_TURMA,
 ID_DISCIPLINAS)
 
 VALUES
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5),
(1, 3),
(2, 1),
(3, 2);

INSERT INTO TURMAS
(ID_TURMA,
 NOME_DA_TURMA,
 ANO_LETIVO,
 ID_PROFESSOR_ORIENTADOR)
 
 VALUES 
(1, 'Turma A', 2023, 1),
(2, 'Turma B', 2023, 2),
(3, 'Turma C', 2023, 3),
(4, 'Turma D', 2023, 4),
(5, 'Turma E', 2023, 5);

SELECT * FROM ALUNOS ORDER BY nome_do_aluno ASC;
SELECT * FROM PROFESSORES;
SELECT * FROM DISCIPLINAS where carga_horaria > 40;

SELECT * FROM TURMAS;
SELECT * FROM TURMAS_ALUNOS;
SELECT * FROM NOTAS where valor_da_nota > 6 and valor_da_nota < 8;

SELECT * FROM TURMAS_DISCIPLINAS;

 
 
 
 
 
 
 
 
 
