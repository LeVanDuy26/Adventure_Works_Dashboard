# Adventure Works Dashboard

Dự án Power BI Dashboard phân tích dữ liệu bán hàng của Adventure Works - một công ty bán lẻ xe đạp và phụ kiện thể thao.

## Xem Dashboard

**[Xem Dashboard trực tuyến](https://app.powerbi.com/reportEmbed?reportId=f337ad28-72a3-4800-938b-7e08ab906250&autoAuth=true&ctid=e7572e92-7aee-4713-a3c4-ba64888ad45f)**

## Cấu trúc Dự án

```
Adventure_Works_Dashboard/
├── 1.Data/                          # Thư mục chứa dữ liệu nguồn
│   ├── Sales Data/                  # Dữ liệu bán hàng theo năm
│   │   ├── AdventureWorks Sales Data 2020.csv
│   │   ├── AdventureWorks Sales Data 2021.csv
│   │   └── AdventureWorks Sales Data 2022.csv
│   ├── AdventureWorks Calendar Lookup.csv
│   ├── AdventureWorks Customer Lookup.csv
│   ├── AdventureWorks Product Lookup.csv
│   ├── AdventureWorks Product Categories Lookup.csv
│   ├── AdventureWorks Product Subcategories Lookup.csv
│   ├── AdventureWorks Region.csv
│   └── AdventureWorks Returns Data.csv
├── 2.Dashboard/                     # Thư mục chứa file Power BI
│   ├── Adventure_Works.pbix         # File Power BI Desktop
│   └── Bối Cảnh Và Yêu Cầu.pdf     # Tài liệu yêu cầu dự án
├── 3. Image/                         # Hình ảnh dashboard
│   ├── Overview.png                 # Trang tổng quan
│   ├── Customer.png                 # Trang phân tích khách hàng
│   └── Product.png                  # Trang phân tích sản phẩm
└── README.md                         # File này
```

## Cấu trúc Dữ liệu

### Fact Tables (Bảng Sự kiện)

#### Sales Data (2020-2022)
Dữ liệu giao dịch bán hàng trong 3 năm (2020-2022)
- `OrderDate`: Ngày đặt hàng
- `StockDate`: Ngày nhập kho
- `OrderNumber`: Số đơn hàng
- `OrderLineItem`: Số dòng trong đơn hàng
- `ProductKey`: Khóa sản phẩm
- `CustomerKey`: Khóa khách hàng
- `TerritoryKey`: Khóa khu vực
- `OrderQuantity`: Số lượng đặt hàng

#### Returns Data
Dữ liệu trả hàng
- `ReturnDate`: Ngày trả hàng
- `TerritoryKey`: Khóa khu vực
- `ProductKey`: Khóa sản phẩm
- `ReturnQuantity`: Số lượng trả hàng

### Dimension Tables (Bảng Chiều)

#### Customer Lookup
Thông tin chi tiết về khách hàng
- Thông tin cá nhân: `CustomerKey`, `Prefix`, `FirstName`, `LastName`, `BirthDate`
- Nhân khẩu học: `MaritalStatus`, `Gender`, `EmailAddress`
- Kinh tế xã hội: `AnnualIncome`, `TotalChildren`, `EducationLevel`, `Occupation`, `HomeOwner`

#### Product Lookup
Thông tin sản phẩm
- `ProductKey`, `ProductSubcategoryKey`, `ProductSKU`
- `ProductName`, `ModelName`, `ProductDescription`
- `ProductColor`, `ProductSize`, `ProductStyle`
- `ProductCost`, `ProductPrice`

#### Product Categories & Subcategories
Phân loại sản phẩm
- **Categories**: Bikes, Components, Clothing, Accessories
- **Subcategories**: 37 subcategories bao gồm Mountain Bikes, Road Bikes, Helmets, Jerseys, Socks, v.v.

#### Region
Thông tin địa lý
- `SalesTerritoryKey`, `Region`, `Country`, `Continent`
- **11 Territories**: 6 vùng Hoa Kỳ, Canada, France, Germany, Australia, United Kingdom

#### Calendar Lookup
Bảng ngày tháng để phân tích theo thời gian
- `Date`: Ngày trong khoảng thời gian từ 2020-2022

## Các Trang Dashboard

### 1. Overview (Tổng quan)
Trang tổng quan cung cấp cái nhìn tổng thể về hiệu suất kinh doanh:
- Tổng doanh thu, số lượng đơn hàng, số lượng sản phẩm bán ra
- Phân tích xu hướng theo thời gian
- Phân tích theo khu vực địa lý
- Top sản phẩm bán chạy
- Phân tích trả hàng

### 2. Customer (Khách hàng)
Trang phân tích khách hàng tập trung vào:
- Phân tích nhân khẩu học (giới tính, độ tuổi, tình trạng hôn nhân)
- Phân tích theo thu nhập và nghề nghiệp
- Phân tích hành vi mua hàng theo nhóm khách hàng
- Customer segmentation

### 3. Product (Sản phẩm)
Trang phân tích sản phẩm bao gồm:
- Phân tích doanh thu và lợi nhuận theo danh mục
- Top sản phẩm bán chạy
- Phân tích theo màu sắc, kích thước, style
- Tỷ lệ trả hàng theo sản phẩm
- Phân tích margin (lợi nhuận)

## Công nghệ Sử dụng

- **Power BI Desktop**: Để tạo và phát triển dashboard
- **Power BI Service**: Để publish và chia sẻ dashboard online
- **CSV Files**: Dữ liệu nguồn dạng CSV
- **DAX (Data Analysis Expressions)**: Để tạo các measures và calculated columns

## Mô hình Dữ liệu

Dashboard sử dụng mô hình **Star Schema** với:
- **1 Fact Table**: Sales Data (kết nối với Returns Data)
- **5 Dimension Tables**: Customer, Product, Calendar, Region, Product Categories/Subcategories

Các quan hệ được thiết lập thông qua các khóa (Keys) giữa Fact Table và Dimension Tables.

## Hướng dẫn Sử dụng

### Mở Dashboard trong Power BI Desktop

1. Mở file `2.Dashboard/Adventure_Works.pbix` bằng Power BI Desktop
2. Đảm bảo các file CSV trong thư mục `1.Data` vẫn ở đúng vị trí
3. Nếu có lỗi kết nối dữ liệu, kiểm tra lại đường dẫn đến các file CSV

### Xem Dashboard Online

Truy cập link: [Xem Dashboard](https://app.powerbi.com/reportEmbed?reportId=f337ad28-72a3-4800-938b-7e08ab906250&autoAuth=true&ctid=e7572e92-7aee-4713-a3c4-ba64888ad45f)

## Ghi chú

- Dữ liệu bao phủ 3 năm: 2020, 2021, 2022
- Dashboard hỗ trợ tương tác với các slicers và filters
- Có thể drill-down vào chi tiết từ các visualizations
- Tất cả các measures và calculations được tối ưu hóa cho hiệu suất

## Tác giả

Dự án được phát triển cho mục đích học tập và phân tích dữ liệu bán hàng.

---
