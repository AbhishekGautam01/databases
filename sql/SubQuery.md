# Sub Query aka Inner Query 
* It's a query nested inside another statement such as **SELECT, INSERT, UPDATE or DELETE** 
* The sub query must be always enclosed inside parenthesis ()
* A sub query can be nested inside another sub query. SQL server supports 32 level of nesting. 
* A sub query **can be used in following places** 
    1. **An Expression** 
    ```
    SELECT 
        order_id, 
        order_date, 
        (
            SELECT 
                MAX(list_price)
            FROM
                sales.order_items i
            WHERE 
                i.order_id = o.order_id
        ) as max_list_price
    FROM 
        sales.orders o 
    order by order_date desc;
    ```
    2. With **IN** or **NOT IN** 
    3. With **Any** ot **All** 
    4. With **Exists or NOT Exists**: `WHERE [NOT] EXISTS (sub-query)`
    5. In **Update, Delete & Insert** 
    6. In **From** Clause
    