-- 1 consultar todos os produtos existentes na loja
select* from product;



-- 2 consultar os nomes de todos os usuarios 
select name from users; 


-- 3 consultar as lojas que vendem produtos
SELECT name
FROM store
WHERE pk_sid IN (SELECT DISTINCT fk_sid FROM Product);

-- 4 Consultar os endereços relacionando com os clientes;
SELECT
    u.name AS customer_name,
    a.*
FROM
    Address a
JOIN
    users u ON u.pk_userid = a.fk_userid;

 

-- 5 Consultar todos os produtos do tipo laptop;
SELECT *
FROM Product
WHERE type = 'laptop';

 

--  6 Consultar o endereço, hora de inicio (start time) e hora final (end time) dos pontos de serviço da
-- mesma cidade que o usuário cujo ID é 5.

 

SELECT
    sp.pk_spid AS service_point_id,
    a.streetaddr AS service_point_address,
    a.startTime AS service_point_start_time,
    a.endTime AS service_point_end_time
FROM
    servicePoint sp
JOIN
    Address a ON sp.pk_spid = a.fk_userid
JOIN
    users u ON a.fk_userid = u.pk_userid
WHERE
    u.pk_userid = 5;

 

-- 7 Consultar a quantidade total de produtos que foram colocados no carrinho (shopping cart),
-- considerando a loja com ID (sid) igual a 8.

 

SELECT SUM(quantity) AS total_quantity
FROM Save_to_Shopping_Cart
WHERE pk_pid IN (SELECT pk_pid FROM Product WHERE fk_sid = 8);

 

-- 8 Consultar os comentários do produto 123456789.

 

SELECT *
FROM comments
WHERE fk_pid = 123456789;

 

 
