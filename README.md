# normaliza

Tabelas e dados

CREATE TABLE veiculos (
    codLocacao INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    veiculo VARCHAR(100) NOT NULL,
    cor VARCHAR(100) NOT NULL,
    placa VARCHAR(50) NOT NULL,
    diaria DECIMAL(9,2) NOT NULL,
    cliente VARCHAR(100) NOT NULL,
    cpf VARCHAR(15) NOT NULL, -- Assuming typical CPF length
    nascimento DATE NOT NULL,
    dia INT NOT NULL,
    total DECIMAL(9,2) NOT NULL
);

create table cliente(
	cpf varchar(100) primary key not null,
	nome varchar(100) not null,
	nascimento date 
);
    
CREATE TABLE veiculo (
    cod_locacao INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    veiculo VARCHAR(100) NOT NULL,
    cor VARCHAR(100) NOT NULL,
    placa VARCHAR(100) NOT NULL,
    diaria DECIMAL(9,2) NOT NULL,
    cpf_cli VARCHAR(100) NOT NULL,
    dia INT NOT NULL,
    total DECIMAL(9,2) NOT NULL,
    FOREIGN KEY (cpf_cli) REFERENCES cliente(cpf)
);


--------------------------------------------------------------------------------------------------------------------------------------------


INSERT INTO cliente (cpf, nome, nascimento) VALUES
('123.456.789-01', 'Ariano Sussuna', '2022-05-21'),
('543.765.987-23', 'Grace Hopper', '2002-04-29'),
('987.654.321-90', 'Richard Feynman', '2001-10-12'),
('432.765.678-67', 'Edgar Poe', '1998-12-14'),
('927.384.284-44', 'Gordon Freeman', '1984-11-26');

SELECT * FROM cliente;


INSERT INTO veiculo (veiculo, cor, placa, diaria, cpf_cliente, dia, total) VALUES
('Fusca', 'Preto', 'WER-3456', 30.00, '123.456.789-01', 3, 90.00),
('Variante', 'Rosa', 'FDS-8384', 60.00, '543.765.987-23', 7, 420.00),
('Comodoro', 'Preto', 'CVB-9933', 20.00, '987.654.321-90', 1, 20.00),
('Delorean', 'Azul', 'FGH-2256', 30.00, '123.456.789-01', 3, 90.00),
('Brasilia', 'Amarela', 'DDI-3948', 45.00, '927.384.284-44', 7, 315.00);

SELECT * FROM veiculo;


-----------------------------------------------------------------------------------------------------------------------------------------

CREATE VIEW Todas_locacoes AS
SELECT * FROM veiculo
JOIN cliente ON cliente.cpf = veiculo.cpf_cliente;

SELECT * FROM Todas_locacoes;

