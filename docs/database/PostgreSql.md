# PostgreSql
1.[Jsonb数组字段查询替换](#Jsonb数组字段查询替换)    

## Jsonb数组字段查询替换  
```sql
-- column_name 值类似 ["https://aaaaaaa/project-file/8be8cfbc2fae46c497192d8aedcf705d.jpg"]
UPDATE table_name
SET column_name = (
    SELECT jsonb_agg(
        CASE
            -- 当值包含 'aaaaaaa' 时，替换为 'bbbbbbb'
            WHEN value LIKE '%aaaaaaa%' THEN replace(value, 'aaaaaaa', 'bbbbbbb')
            -- 其他情况下，保持值不变
            ELSE value
        END
    )
    FROM jsonb_array_elements_text(column_name) AS value
)
WHERE EXISTS (
    SELECT 1
    FROM jsonb_array_elements_text(column_name) AS url
    -- 直接在 LIKE 子句中使用 url，因为它已经是文本类型
    WHERE url LIKE '%aaaaaaa%'
);
```