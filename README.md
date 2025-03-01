Exibe as informações básicas dos veículos, como marca, modelo e cor:
SELECT brand, model, color FROM Vehicles;

Faz uma junção entre as tabelas de veículos e clientes, mostrando o proprietário de cada veículo:
SELECT v.brand, v.model, v.plate, c.first_name, c.last_name
FROM Vehicles v
JOIN Customers c ON v.customer_id = c.customer_id;

Mostra quantos veículos estão cadastrados para cada cliente:
SELECT c.first_name, c.last_name, COUNT(v.vehicle_id) AS vehicle_count
FROM Customers c
JOIN Vehicles v ON c.customer_id = v.customer_id
GROUP BY c.customer_id;

Mostra o histórico completo de manutenção de cada veículo, ordenado pela data:
SELECT v.brand, v.model, v.plate, vsh.service_date, vsh.service_description, vsh.parts_used
FROM VehicleServiceHistory vsh
JOIN Vehicles v ON vsh.vehicle_id = v.vehicle_id
ORDER BY vsh.service_date DESC;


Lista os fornecedores, classificando-os pela quantidade de peças fornecidas:
SELECT s.name, COUNT(p.part_id) AS total_parts
FROM Suppliers s
JOIN Parts p ON s.supplier_id = p.category_id
GROUP BY s.supplier_id
ORDER BY total_parts DESC;
