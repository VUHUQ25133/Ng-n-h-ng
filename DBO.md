🔹 1. Customer (dbo.Customer)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| CustomerID | int | — | 4 | 11 | Primary key, unique identifier for Customer | 1 | PK, not null |
| Name | string | — | 100 | 100 | Customer's name | "John Nguyen" | not null |
| ContactInformation | string | — | 100 | 100 | Customer's phone or email | "090-123-1234" | not null |
| RewardPoints | int | — | 4 | 11 | Loyalty points for promotions | 200 | 0 <= points <= 10000 |

🔹 2. Employee (dbo.Employee)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| EmployeeID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| FullName | string | — | 100 | 100 | Employee's full name | "Mike Tran" | not null |
| Position | string | — | 50 | 50 | Job title or role | "Manager" | not null |
| PhoneNumber | string | — | 20 | 20 | Contact phone | "090-888-8888" | not null |
| Email | string | — | 100 | 100 | Company email | "mike@example.com" | unique |
| StoreID | int | — | 4 | 11 | Foreign key to Store | 1 | must match existing Store |

🔹 3. DeliveryProcess (dbo.DeliveryProcess)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| DeliveryID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| OrderID | int | — | 4 | 11 | Foreign key to Order | 5 | must match existing Order |
| DeliveryStatus | string | — | 20 | 20 | Delivery state | "Delivered" | in ('Pending','Delivered') |
| DeliveryTime | datetime | "YYYY-MM-DD HH:MI:SS" | 8 | 20 | Delivery timestamp | "2025-01-12 01:51:00" | <= current datetime |
| ShipperName | string | — | 100 | 100 | Name of delivery person | "Mike Shipper" | not null |
| PartnerID | int | — | 4 | 11 | Foreign key to DeliveryPartner | 1 | must match existing DeliveryPartner |

🔹 4. Order (dbo.Order)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| OrderID | int | — | 4 | 11 | Primary key | 5 | PK, not null |
| OrderTime | datetime | "YYYY-MM-DD HH:MI:SS" | 8 | 20 | Date and time of order | "2025-01-12 00:00:00" | <= current datetime |
| PaymentMethod | string | — | 20 | 20 | Payment Type | "Cash" | in ('Cash','Card') |
| Status | string | — | 20 | 20 | Order's delivery state | "Processing" | in ('Processing','Delivered') |
| CustomerID | int | — | 4 | 11 | Foreign key to Customer | 1 | must match existing Customer |
| StoreID | int | — | 4 | 11 | Foreign key to Store | 1 | must match existing Store |

🔹 5. DrinkRecipe (dbo.DrinkRecipe)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| FoodDrinkID | int | — | 4 | 11 | PK, Foreign key to FoodDrink | 1 | PK, must match existing |
| RawMaterialID | int | — | 4 | 11 | PK, Foreign key to RawMaterial | 1 | PK, must match existing |
| Quantity | int | — | 4 | 11 | Quantity of raw material | 10 | > 0 |

🔹 6. Store (dbo.Store)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| StoreID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| Name | string | — | 100 | 100 | Name of store | "The Coffee House – Hồ Tùng Mậu" | not null |
| Location | string | — | 100 | 100 | Location | "Hồ Tùng Mậu" | not null |
| ContactInformation | string | — | 20 | 20 | Phone or contact | "001-967-162-7270x275" | not null |

🔹 7. RawMaterial (dbo.RawMaterial)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| MaterialID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| Name | string | — | 100 | 100 | Material's name | "Coffee Beans" | not null |
| Unit | string | — | 10 | 10 | Unit of measure | "g" | not null |

🔹 8. OrderDetail (dbo.OrderDetail)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| DetailID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| OrderID | int | — | 4 | 11 | Foreign key to Order | 5 | must match existing Order |
| FoodDrinkID | int | — | 4 | 11 | Foreign key to FoodDrink | 1 | must match existing FoodDrink |
| Quantity | int | — | 4 | 11 | Quantity of item | 4 | > 0 |
| Size | string | — | 10 | 10 | Size of drink | "Small" | in ('Small','Medium','Large') |
| Topping | string | — | 50 | 50 | Additional toppings | "None" | optional |

🔹 9. DeliveryPartner (dbo.DeliveryPartner)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| PartnerID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| Name | string | — | 100 | 100 | Company name | "ShopeeFood" | not null |
| Contact | string | — | 20 | 20 | Phone or contact | "+1-812-252-8127" | not null |
| Rating | float | — | 4 | 5 | Rating score (0-5) | 4.71 | 0 <= Rating <= 5 |

🔹 10. Supplier (dbo.Supplier)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| SupplierID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| Name | string | — | 100 | 100 | Supplier's name | "Cau Dat Farm" | not null |
| Contact | string | — | 20 | 20 | Contact phone | "001-903-693-4229" | not null |

🔹 11. Inventory (dbo.Inventory)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| RawMaterialID | int | — | 4 | 11 | PK, Foreign key to RawMaterial | 3 | PK, must match existing |
| StoreID | int | — | 4 | 11 | PK, Foreign key to Store | 4 | PK, must match existing |
| Quantity | int | — | 4 | 11 | Quantity in stock | 22 | 0 <= Quantity |

🔹 12. FoodDrink (dbo.FoodDrink)
|Data Item|Data Type|Data Format|Number of Bytes for Storage|Size for Display|Description|Example|Validation|
|-|-|-|-|-|-|-|-|
| FoodDrinkID | int | — | 4 | 11 | Primary key | 1 | PK, not null |
| Name | string | — | 100 | 100 | Menu item name | "Latte Almond" | not null |
| Category | string | — | 50 | 50 | Type of drink | "Cà Phê Máy" | not null |
| Price | int | — | 4 | 11 | Selling price | 59000 | > 0 |