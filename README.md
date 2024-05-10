# Casino
-Alejandro Machado, Email: Ale_machado0511@hotmail.com

-Lucas Sosa, Email: Lucassosa2019@hotmail.com

Temática: Plataforma de agentes de casino virtual.

Descripción de la temática: La página que estamos creando es una plataforma de agente de casino virtual en la cuál se podría crear un agente, eliminarlo, ver sus datos, y lo mismo con el usuario.

La relación se encuentra en que un agente puede tener 0 o muchos clientes un cliente puede tener 0 o 1 agente (clave foránea).

Imagen de entidad relación:

![WhatsApp Image 2024-05-04 at 18 00 19](https://github.com/DAleMF05/Casino/assets/166235026/53e45133-50c3-430e-b359-e870ce67394f)

--
-- Estructura de tabla para la tabla `agentes`
--

CREATE TABLE `agentes` (
  `id_agente` int(11) NOT NULL,
  `nombre` varchar(250) NOT NULL,
  `saldo` double(10,2) NOT NULL,
  `email` varchar(250) NOT NULL,
  `activado` tinyint(1) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;


--
-- Estructura de tabla para la tabla `cliente`
--

CREATE TABLE `cliente` (
  `id_cliente` int(11) NOT NULL,
  `nombre_usuario` varchar(100) NOT NULL,
  `saldo` double(10,2) NOT NULL,
  `activado` tinyint(1) NOT NULL,
  `id_agente` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Índices para tablas volcadas
--

--
-- Indices de la tabla `agentes`
--
ALTER TABLE `agentes`
  ADD PRIMARY KEY (`id_agente`);

--
-- Indices de la tabla `cliente`
--
ALTER TABLE `cliente`
  ADD PRIMARY KEY (`id_cliente`),
  ADD KEY `fk_cliente_agentes` (`id_agente`);

--
-- AUTO_INCREMENT de las tablas volcadas
--

--
-- AUTO_INCREMENT de la tabla `agentes`
--
ALTER TABLE `agentes`
  MODIFY `id_agente` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT de la tabla `cliente`
--
ALTER TABLE `cliente`
  MODIFY `id_cliente` int(11) NOT NULL AUTO_INCREMENT;

--
-- Restricciones para tablas volcadas
--

--
-- Filtros para la tabla `cliente`
--
ALTER TABLE `cliente`
  ADD CONSTRAINT `fk_cliente_agentes` FOREIGN KEY (`id_cliente`) REFERENCES `agentes` (`id_agente`);

