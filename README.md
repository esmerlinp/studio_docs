# studio_docs

-- =============================================
-- Ejemplos de uso:
-- =============================================

-- 1. Resumen de todos los módulos con estadísticas
-- SELECT * FROM sp_permisos_usuario(1, NULL, NULL, NULL, TRUE);

-- 2. Permisos agrupados de un módulo específico
-- SELECT * FROM sp_permisos_usuario(1, 'a1b2c3d4-e5f6-7890-abcd-ef1234567890'::UUID, NULL, NULL, FALSE);

-- 3. Permisos de una pantalla específica
-- SELECT * FROM sp_permisos_usuario(1, 'uuid-modulo'::UUID, 'uuid-pantalla'::UUID, NULL, FALSE);

-- 4. Permisos de una funcionalidad específica
-- SELECT * FROM sp_permisos_usuario(1, NULL, NULL, 'uuid-funcionalidad'::UUID, FALSE);

-- 5. Todos los permisos detallados del usuario
-- SELECT * FROM sp_permisos_usuario(1, NULL, NULL, NULL, FALSE);

-- 6. Solo permisos permitidos de un usuario
-- SELECT * FROM sp_permisos_usuario(1, NULL, NULL, NULL, FALSE)
-- WHERE bpermitido = TRUE;

-- 7. Verificar si tiene un permiso específico
-- SELECT EXISTS(
--     SELECT 1 FROM sp_permisos_usuario(1, NULL, NULL, 'uuid-funcionalidad'::UUID, FALSE)
--     WHERE bpermitido = TRUE
-- ) as tiene_permiso;

-- 8. Contar permisos activos por módulo
-- SELECT 
--     smodulo,
--     COUNT(*) FILTER (WHERE bpermitido = TRUE) as permisos_activos,
--     COUNT(*) as total_funcionalidades
-- FROM sp_permisos_usuario(1, NULL, NULL, NULL, FALSE)
-- GROUP BY smodulo, iordenmodulo
-- ORDER BY iordenmodulo;
