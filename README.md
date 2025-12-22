# studio_docs

-- =============================================
-- Ejemplos de uso
-- =============================================

/*
-- 1. Resumen de módulos (¿a qué módulos tiene acceso?)
SELECT 
    smodulo,
    bpermitido,
    itotalpantallas,
    itotalpermisosactivos
FROM fn_permisos_usuario(
    p_idusuario := 1,
    p_uuidcliente := 'aa1c7a4c-da0c-4407-93ce-4f8574fb07d1',
    p_bresumenmodulos := TRUE
)
WHERE bpermitido = TRUE;

-- 2. Permisos de un módulo específico
SELECT 
    smodulo,
    bpermitido
FROM fn_permisos_usuario(
    p_idusuario := 1,
    p_uuidcliente := 'aa1c7a4c-da0c-4407-93ce-4f8574fb07d1',
    p_uuidmodulo := 'uuid-del-modulo'
);

-- 3. Todas las funcionalidades permitidas
SELECT 
    smodulo,
    spantalla,
    sfuncionalidad,
    scodigofuncionalidad
FROM fn_permisos_usuario(
    p_idusuario := 1,
    p_uuidcliente := 'aa1c7a4c-da0c-4407-93ce-4f8574fb07d1'
)
WHERE bpermitido = TRUE
ORDER BY smodulo, spantalla, sfuncionalidad;

-- 4. Validar permiso específico
SELECT bpermitido
FROM fn_permisos_usuario(
    p_idusuario := 1,
    p_uuidcliente := 'aa1c7a4c-da0c-4407-93ce-4f8574fb07d1',
    p_uuidfuncionalidad := 'uuid-de-funcionalidad'
);

-- 5. Permisos de una pantalla
SELECT 
    sfuncionalidad,
    scodigofuncionalidad,
    bpermitido
FROM fn_permisos_usuario(
    p_idusuario := 1,
    p_uuidcliente := 'aa1c7a4c-da0c-4407-93ce-4f8574fb07d1',
    p_uuidpantalla := 'uuid-de-pantalla'
);
*/
