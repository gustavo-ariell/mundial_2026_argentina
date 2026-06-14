-- ================================================================
--  MUNDIAL FIFA 2026 — SELECCIÓN ARGENTINA  ·  GRUPO J
--  Motor: MariaDB  ·  Ejecutable en DBeaver
--
--  · Plantel de 26 confirmado por Scaloni
--  · Fechas, rivales y sedes oficiales FIFA del Grupo J
--  · Ciudad de origen real de cada jugador
--  · Resultados de los 3 partidos: FICTICIOS
--  · Messi: máximo goleador de la fase de grupos (5 goles, 2asis)
--  · Sedes con nombres oficiales FIFA World Cup 2026 (citation:1)
-- ================================================================

DROP DATABASE IF EXISTS mundial_2026_argentina;
CREATE DATABASE mundial_2026_argentina
    DEFAULT CHARACTER SET utf8mb4
    COLLATE utf8mb4_unicode_ci;

USE mundial_2026_argentina;

-- ============================= DDL ============================

CREATE TABLE dirigentes (
    id_dirigente    INT           PRIMARY KEY AUTO_INCREMENT,
    nombre          VARCHAR(100)  NOT NULL,
    cargo           VARCHAR(100)  NOT NULL,
    edad            INT           NOT NULL,
    nacionalidad    VARCHAR(50)   NOT NULL,
    anios_en_cargo  INT           NOT NULL
) ENGINE=InnoDB;

CREATE TABLE cuerpo_tecnico (
    id_tecnico         INT           PRIMARY KEY AUTO_INCREMENT,
    nombre             VARCHAR(100)  NOT NULL,
    cargo              VARCHAR(100)  NOT NULL,
    edad               INT           NOT NULL,
    nacionalidad       VARCHAR(50)   NOT NULL,
    experiencia_anios  INT           NOT NULL,
    id_dirigente       INT,
    FOREIGN KEY (id_dirigente) REFERENCES dirigentes (id_dirigente)
) ENGINE=InnoDB;

CREATE TABLE futbolistas (
    id_futbolista  INT           PRIMARY KEY,
    nombre         VARCHAR(100)  NOT NULL,
    dorsal         INT           NOT NULL,
    posicion       VARCHAR(50)   NOT NULL,
    edad           INT           NOT NULL,
    ciudad_origen  VARCHAR(100)  NOT NULL,   -- ◄ NUEVO CAMPO
    club           VARCHAR(100)  NOT NULL,
    id_tecnico     INT,
    FOREIGN KEY (id_tecnico) REFERENCES cuerpo_tecnico (id_tecnico)
) ENGINE=InnoDB;

CREATE TABLE partidos (
    id_partido  INT           PRIMARY KEY AUTO_INCREMENT,
    rival       VARCHAR(100)  NOT NULL,
    fecha       DATE          NOT NULL,
    estadio     VARCHAR(150)  NOT NULL,
    ciudad      VARCHAR(100)  NOT NULL,
    fase        VARCHAR(50)   NOT NULL
) ENGINE=InnoDB;

CREATE TABLE futbolista_partido (
    id_futbolista    INT         NOT NULL,
    id_partido       INT         NOT NULL,
    goles            INT         DEFAULT 0,
    asistencias      INT         DEFAULT 0,
    minutos_jugados  INT         DEFAULT 0,
    titular          TINYINT(1)  DEFAULT 0,
    PRIMARY KEY (id_futbolista, id_partido),
    FOREIGN KEY (id_futbolista) REFERENCES futbolistas (id_futbolista),
    FOREIGN KEY (id_partido)    REFERENCES partidos    (id_partido)
) ENGINE=InnoDB;


-- ============================= DML ============================

-- ─────────────────────────────────────────────────────────────
--  DIRIGENTES
-- ─────────────────────────────────────────────────────────────
INSERT INTO dirigentes (nombre, cargo, edad, nacionalidad, anios_en_cargo) VALUES
('Claudio Tapia',    'Presidente AFA',      58, 'Argentina', 9),
('Daniel Angelici',  'Vicepresidente AFA',  62, 'Argentina', 3),
('Marcelo Achile',   'Secretario General',  55, 'Argentina', 5);


-- ─────────────────────────────────────────────────────────────
--  CUERPO TÉCNICO
-- ─────────────────────────────────────────────────────────────
INSERT INTO cuerpo_tecnico
    (nombre, cargo, edad, nacionalidad, experiencia_anios, id_dirigente) VALUES
('Lionel Scaloni', 'Director Técnico',          48, 'Argentina', 8,  1),
('Pablo Aimar',    'Ayudante de Campo',         46, 'Argentina', 8,  1),
('Walter Samuel',  'Ayudante de Campo',         48, 'Argentina', 7,  1),
('Martín Tocalli', 'Preparador de Arqueros',    52, 'Argentina', 12, 1);


-- ─────────────────────────────────────────────────────────────
--  FUTBOLISTAS — 26 convocados oficiales
--  + Ciudad de origen REAL de cada jugador
--
--  id_tecnico:
--    1 = Scaloni  → Delanteros
--    2 = Aimar    → Mediocampistas
--    3 = Samuel   → Defensores
--    4 = Tocalli  → Arqueros
-- ─────────────────────────────────────────────────────────────

-- ARQUEROS  (id_tecnico 4)
INSERT INTO futbolistas
    (id_futbolista, nombre, dorsal, posicion, edad, ciudad_origen, club, id_tecnico) VALUES
( 1, 'Gerónimo Rulli',      1,  'Arquero', 34, 'La Plata, Buenos Aires',          'Olympique de Marsella',  4),
(12, 'Juan Musso',          12, 'Arquero', 32, 'San Nicolás, Buenos Aires',       'Atlético de Madrid',     4),
(23, 'Emiliano Martínez',   23, 'Arquero', 33, 'Mar del Plata, Buenos Aires',     'Aston Villa',            4);

-- DEFENSORES  (id_tecnico 3)
INSERT INTO futbolistas
    (id_futbolista, nombre, dorsal, posicion, edad, ciudad_origen, club, id_tecnico) VALUES
( 2, 'Marcos Senesi',       2,  'Defensor', 29, 'Concordia, Entre Ríos',           'Tottenham',              3),
( 3, 'Nicolás Tagliafico',  3,  'Defensor', 33, 'Buenos Aires',                    'Olympique de Lyon',      3),
( 4, 'Gonzalo Montiel',     4,  'Defensor', 29, 'Sarandí, Buenos Aires',           'River Plate',            3),
( 6, 'Lisandro Martínez',   6,  'Defensor', 28, 'Gualeguay, Entre Ríos',           'Manchester United',      3),
(13, 'Cristian Romero',     13, 'Defensor', 28, 'Córdoba',                         'Tottenham',              3),
(19, 'Nicolás Otamendi',    19, 'Defensor', 38, 'Buenos Aires',                    'Benfica',                3),
(25, 'Facundo Medina',      25, 'Defensor', 27, 'Buenos Aires',                    'Olympique de Marsella',  3),
(26, 'Nahuel Molina',       26, 'Defensor', 28, 'Embalse, Córdoba',                'Atlético de Madrid',     3);

-- MEDIOCAMPISTAS  (id_tecnico 2)
INSERT INTO futbolistas
    (id_futbolista, nombre, dorsal, posicion, edad, ciudad_origen, club, id_tecnico) VALUES
( 5, 'Leandro Paredes',     5,  'Mediocampista', 31, 'San Justo, Buenos Aires',         'Boca Juniors',           2),
( 7, 'Rodrigo De Paul',     7,  'Mediocampista', 32, 'Sarandí, Buenos Aires',           'Inter Miami',            2),
( 8, 'Valentín Barco',      8,  'Mediocampista', 22, 'Veinticinco de Mayo, Buenos Aires','Racing de Estrasburgo',  2),
(11, 'Giovani Lo Celso',    11, 'Mediocampista', 30, 'Rosario, Santa Fe',                'Real Betis',             2),
(14, 'Exequiel Palacios',   14, 'Mediocampista', 27, 'Famaillá, Tucumán',                'Bayer Leverkusen',       2),
(20, 'Alexis Mac Allister', 20, 'Mediocampista', 27, 'Santa Rosa, La Pampa',             'Liverpool',              2),
(24, 'Enzo Fernández',      24, 'Mediocampista', 25, 'San Martín, Buenos Aires',         'Chelsea',                2);

-- DELANTEROS  (id_tecnico 1)
INSERT INTO futbolistas
    (id_futbolista, nombre, dorsal, posicion, edad, ciudad_origen, club, id_tecnico) VALUES
( 9, 'Julián Álvarez',      9,  'Delantero', 26, 'Calchín, Córdoba',                'Atlético de Madrid',  1),
(10, 'Lionel Messi',        10, 'Delantero', 38, 'Rosario, Santa Fe',               'Inter Miami',         1),
(15, 'Nicolás González',    15, 'Delantero', 28, 'Avellaneda, Buenos Aires',        'Atlético de Madrid',  1),
(16, 'Thiago Almada',       16, 'Delantero', 25, 'Ciudadela, Buenos Aires',         'Atlético de Madrid',  1),
(17, 'Giuliano Simeone',    17, 'Delantero', 23, 'Buenos Aires',                    'Atlético de Madrid',  1),
(18, 'Nicolás Paz',         18, 'Delantero', 22, 'Santa Cruz de Tenerife, España',  'Como',                1),
(21, 'José Manuel López',   21, 'Delantero', 25, 'Lanús, Buenos Aires',             'Palmeiras',           1),
(22, 'Lautaro Martínez',    22, 'Delantero', 28, 'Bahía Blanca, Buenos Aires',      'Inter de Milán',      1);


-- ─────────────────────────────────────────────────────────────
--  PARTIDOS — Fase de Grupos (Grupo J)
--  Fechas, rivales y sedes OFICIALES FIFA World Cup 2026 (citation:1)
--  Resultados: FICTICIOS
--
--  Kansas City Stadium → Kansas City, Missouri (citation:1)(citation:8)
--  Dallas Stadium      → Arlington, Texas     (citation:1)
-- ─────────────────────────────────────────────────────────────
INSERT INTO partidos (rival, fecha, estadio, ciudad, fase) VALUES
('Argelia',  '2026-06-16', 'Kansas City Stadium', 'Kansas City, Misuri',       'Fase de Grupos'),
('Austria',  '2026-06-22', 'Dallas Stadium',      'Arlington, Texas',          'Fase de Grupos'),
('Jordania', '2026-06-27', 'Dallas Stadium',      'Arlington, Texas',          'Fase de Grupos');


-- ─────────────────────────────────────────────────────────────
--  FUTBOLISTA_PARTIDO
--
--  Resultados ficticios:
--    Partido 1 : Argentina  3 – 0  Argelia
--    Partido 2 : Argentina  2 – 1  Austria
--    Partido 3 : Argentina  4 – 0  Jordania
--
--  MESSI — Máximo goleador de la fase de grupos:
--    5 goles + 2 asistencias en 3 partidos (270 min)
-- ─────────────────────────────────────────────────────────────


-- ══════════════════════════════════════════════════════════════
--  PARTIDO 1  ·  Argentina 3 – 0 Argelia
--  16 de junio — Kansas City Stadium (citation:8)
--
--  Gol 1:  Messi 15'              (asis. Mac Allister)
--  Gol 2:  Lautaro Martínez 45+2' (asis. Messi)
--  Gol 3:  Messi 62'              (asis. J. Álvarez)
-- ══════════════════════════════════════════════════════════════
INSERT INTO futbolista_partido
    (id_futbolista, id_partido, goles, asistencias, minutos_jugados, titular) VALUES
-- Titulares (11)
(23, 1, 0, 0, 90, 1),   -- E. Martínez
(26, 1, 0, 0, 90, 1),   -- Molina
(13, 1, 0, 0, 90, 1),   -- Romero
( 6, 1, 0, 0, 90, 1),   -- L. Martínez
( 3, 1, 0, 0, 90, 1),   -- Tagliafico
( 7, 1, 0, 0, 80, 1),   -- De Paul
(24, 1, 0, 0, 90, 1),   -- Enzo Fernández
(20, 1, 0, 1, 72, 1),   -- Mac Allister     ← asist. Gol 1
(10, 1, 2, 1, 90, 1),   -- Messi ★          ← Gol 15', asist. 45+2', Gol 62'
( 9, 1, 0, 1, 65, 1),   -- J. Álvarez       ← asist. Gol 3
(22, 1, 1, 0, 90, 1),   -- Lautaro Martínez ← Gol 45+2'
-- Suplentes (3)
(15, 1, 0, 0, 25, 0),   -- N. González      (entró min 65)
(11, 1, 0, 0, 18, 0),   -- Lo Celso         (entró min 72)
( 5, 1, 0, 0, 10, 0);   -- Paredes          (entró min 80)


-- ══════════════════════════════════════════════════════════════
--  PARTIDO 2  ·  Argentina 2 – 1 Austria
--  22 de junio — Dallas Stadium
--
--  Gol 1:  Messi 34'        (de penal)
--  Gol 2:  J. Álvarez 68'  (asis. Mac Allister)
-- ══════════════════════════════════════════════════════════════
INSERT INTO futbolista_partido
    (id_futbolista, id_partido, goles, asistencias, minutos_jugados, titular) VALUES
-- Titulares (11)
(23, 2, 0, 0, 90, 1),   -- E. Martínez
(26, 2, 0, 0, 90, 1),   -- Molina
(13, 2, 0, 0, 90, 1),   -- Romero
( 6, 2, 0, 0, 90, 1),   -- L. Martínez
( 3, 2, 0, 0, 90, 1),   -- Tagliafico
( 7, 2, 0, 0, 90, 1),   -- De Paul
(24, 2, 0, 0, 90, 1),   -- Enzo Fernández
(20, 2, 0, 1, 72, 1),   -- Mac Allister     ← asist. Gol 2
(10, 2, 1, 0, 90, 1),   -- Messi ★          ← Gol 34' (penal)
( 9, 2, 1, 0, 58, 1),   -- J. Álvarez       ← Gol 68'
(15, 2, 0, 0, 80, 1),   -- N. González
-- Suplentes (3)
(22, 2, 0, 0, 32, 0),   -- Lautaro Martínez (entró min 58)
(14, 2, 0, 0, 18, 0),   -- Palacios         (entró min 72)
( 8, 2, 0, 0, 10, 0);   -- Barco            (entró min 80)


-- ══════════════════════════════════════════════════════════════
--  PARTIDO 3  ·  Argentina 4 – 0 Jordania
--  27 de junio — Dallas Stadium
--  (Scaloni rotó gran parte del equipo)
--
--  Gol 1:  Messi 22'              (asis. Paredes)
--  Gol 2:  N. González 40'        (asis. Messi)
--  Gol 3:  Messi 68'              (asis. Palacios)
--  Gol 4:  Lautaro Martínez 85'   (asis. G. Simeone)
-- ══════════════════════════════════════════════════════════════
INSERT INTO futbolista_partido
    (id_futbolista, id_partido, goles, asistencias, minutos_jugados, titular) VALUES
-- Titulares (11) — alineación alternativa
(23, 3, 0, 0, 90, 1),   -- E. Martínez
( 4, 3, 0, 0, 90, 1),   -- Montiel
(19, 3, 0, 0, 90, 1),   -- Otamendi
( 2, 3, 0, 0, 90, 1),   -- Senesi
(25, 3, 0, 0, 90, 1),   -- Medina
(14, 3, 0, 1, 90, 1),   -- Palacios         ← asist. Gol 3
( 5, 3, 0, 1, 90, 1),   -- Paredes          ← asist. Gol 1
( 8, 3, 0, 0, 65, 1),   -- Barco
(10, 3, 2, 1, 90, 1),   -- Messi ★          ← Gol 22', asist. 40', Gol 68'
(22, 3, 1, 0, 75, 1),   -- Lautaro Martínez ← Gol 85'
(15, 3, 1, 0, 55, 1),   -- N. González      ← Gol 40'
-- Suplentes (3)
(17, 3, 0, 1, 35, 0),   -- G. Simeone       (entró min 55) ← asist. Gol 4
(16, 3, 0, 0, 25, 0),   -- Almada           (entró min 65)
(21, 3, 0, 0, 15, 0);   -- J.M. López       (entró min 75)
