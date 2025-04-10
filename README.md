USE [master]
GO
/****** Object:  Database [MobileShopDB_2]    Script Date: 4/9/2025 11:14:02 PM ******/
CREATE DATABASE [MobileShopDB_2]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'MobileShopDB_2', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MobileShopDB_2.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'MobileShopDB_2_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\MobileShopDB_2_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
 WITH CATALOG_COLLATION = DATABASE_DEFAULT, LEDGER = OFF
GO
ALTER DATABASE [MobileShopDB_2] SET COMPATIBILITY_LEVEL = 160
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [MobileShopDB_2].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [MobileShopDB_2] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET ARITHABORT OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET AUTO_CLOSE ON 
GO
ALTER DATABASE [MobileShopDB_2] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [MobileShopDB_2] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [MobileShopDB_2] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET  ENABLE_BROKER 
GO
ALTER DATABASE [MobileShopDB_2] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [MobileShopDB_2] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [MobileShopDB_2] SET  MULTI_USER 
GO
ALTER DATABASE [MobileShopDB_2] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [MobileShopDB_2] SET DB_CHAINING OFF 
GO
ALTER DATABASE [MobileShopDB_2] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [MobileShopDB_2] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [MobileShopDB_2] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [MobileShopDB_2] SET ACCELERATED_DATABASE_RECOVERY = OFF  
GO
ALTER DATABASE [MobileShopDB_2] SET QUERY_STORE = ON
GO
ALTER DATABASE [MobileShopDB_2] SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 30), DATA_FLUSH_INTERVAL_SECONDS = 900, INTERVAL_LENGTH_MINUTES = 60, MAX_STORAGE_SIZE_MB = 1000, QUERY_CAPTURE_MODE = AUTO, SIZE_BASED_CLEANUP_MODE = AUTO, MAX_PLANS_PER_QUERY = 200, WAIT_STATS_CAPTURE_MODE = ON)
GO
USE [MobileShopDB_2]
GO
/****** Object:  Table [dbo].[Cart]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Cart](
	[CartID] [nvarchar](255) NOT NULL,
	[ProductID] [nvarchar](255) NULL,
	[CreateDate] [datetime] NULL,
	[SessionID] [nvarchar](255) NULL,
	[Soluong] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[CartID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[OrderDetails]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[OrderDetails](
	[OrderDetailID] [nvarchar](255) NOT NULL,
	[OrderID] [nvarchar](255) NOT NULL,
	[ProductID] [nvarchar](255) NOT NULL,
	[Quantity] [int] NOT NULL,
	[Price] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[OrderDetailID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Orders]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Orders](
	[OrderID] [nvarchar](255) NOT NULL,
	[UserID] [nvarchar](255) NOT NULL,
	[OrderDate] [datetime] NOT NULL,
	[TotalPrice] [decimal](18, 2) NULL,
	[Status] [nvarchar](255) NULL,
PRIMARY KEY CLUSTERED 
(
	[OrderID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ProductBrand]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ProductBrand](
	[BrandID] [nvarchar](255) NOT NULL,
	[CatalogueID] [nvarchar](255) NOT NULL,
	[BrandName] [nvarchar](50) NULL,
 CONSTRAINT [PK_ProductBrand] PRIMARY KEY CLUSTERED 
(
	[BrandID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ProductCatalogues]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ProductCatalogues](
	[CatalogueID] [nvarchar](255) NOT NULL,
	[CatalogueName] [nvarchar](255) NULL,
PRIMARY KEY CLUSTERED 
(
	[CatalogueID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Products]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Products](
	[ProductID] [nvarchar](255) NOT NULL,
	[Name] [nvarchar](255) NOT NULL,
	[Price] [int] NOT NULL,
	[Description] [nvarchar](255) NULL,
	[Quantity] [int] NULL,
	[Image_path] [nvarchar](255) NULL,
	[color] [nvarchar](255) NULL,
	[size] [nvarchar](255) NULL,
	[CatalogueID] [nvarchar](255) NULL,
	[BrandID] [nvarchar](255) NULL,
PRIMARY KEY CLUSTERED 
(
	[ProductID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Roles]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Roles](
	[RoleID] [bit] NOT NULL,
	[RoleName] [nvarchar](255) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[RoleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Sessions]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Sessions](
	[SessionID] [nvarchar](255) NOT NULL,
	[UserID] [nvarchar](255) NULL,
PRIMARY KEY CLUSTERED 
(
	[SessionID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UserID] [nvarchar](255) NOT NULL,
	[Account] [nvarchar](255) NOT NULL,
	[Password] [nvarchar](255) NOT NULL,
	[Name] [nvarchar](255) NOT NULL,
	[RoleID] [bit] NULL,
	[PhoneNumber] [nvarchar](20) NOT NULL,
	[Address] [nvarchar](100) NOT NULL,
	[Email] [nvarchar](100) NULL,
PRIMARY KEY CLUSTERED 
(
	[UserID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Variants]    Script Date: 4/9/2025 11:14:02 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Variants](
	[ProductID] [nvarchar](255) NOT NULL,
	[Color] [nvarchar](50) NOT NULL,
	[Size] [nvarchar](50) NOT NULL,
	[Price] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[ProductID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'0316dda8-a39f-484a-b443-ad7a813dd96d', N'b64288ae-f3d2-4134-ad1b-bb370c5bac5c', N'6e51f81f-98a0-4cfc-ba08-15a57107d5ff', 1, 300000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'1fd495cb-5259-4596-9990-d0f4b4111527', N'292417b0-a104-4fd9-80a0-823fbb061097', N'6e51f81f-98a0-4cfc-ba08-15a57107d5ff', 1, 300000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'3a2161ea-8872-4720-b266-8bdd2f9be26b', N'f39537c3-acf6-4cc2-b579-c1828461b36d', N'409b5469-d3d5-4a8e-b08e-14c94a3ec7d1', 1, 24450000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'4225b06e-5082-41cb-bd16-7524ae132c8c', N'25f7c889-e1e6-4b61-b0ef-3b2e9221151e', N'6e51f81f-98a0-4cfc-ba08-15a57107d5ff', 1, 300000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'52dbbe33-34d0-415d-aa18-32cc7103d5db', N'b4a74610-cd48-4f55-902d-197fb404179e', N'ddeb97b2-f1dc-4191-a36f-12eb54259374', 1, 20000000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'58dc1a2d-2731-4524-88c7-37cbc9d8b06e', N'903ab253-ec01-45d9-a23b-5cd8fe285a0f', N'ddeb97b2-f1dc-4191-a36f-12eb54259374', 1, 20000000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'674f660e-4a4d-457c-bcf5-33411fa08a0e', N'76c60abf-3a36-4680-8979-a73d80b2af4f', N'409b5469-d3d5-4a8e-b08e-14c94a3ec7d1', 1, 24450000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'a4e7624f-fe7d-4441-86de-d70c73874937', N'b64288ae-f3d2-4134-ad1b-bb370c5bac5c', N'ddeb97b2-f1dc-4191-a36f-12eb54259374', 2, 40000000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'aaf1c0f9-fa8c-48df-8ecd-9d1ed3eb4ea4', N'903ab253-ec01-45d9-a23b-5cd8fe285a0f', N'6e51f81f-98a0-4cfc-ba08-15a57107d5ff', 1, 300000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'c6556887-6be9-4712-b66a-5566d3e6c9c5', N'c3b85fef-921d-4253-a9b0-8d1ad34f50ce', N'ddeb97b2-f1dc-4191-a36f-12eb54259374', 10, 200000000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'dd626838-bafa-40b8-8574-88312f49b4e5', N'd6fde812-817a-419b-854f-a4e8945c3c04', N'a63144ed-f659-42f4-ada6-b98b6d4c0803', 1, 4290000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'e292485e-1fbc-4ca2-95db-5a5454de85ee', N'c3b85fef-921d-4253-a9b0-8d1ad34f50ce', N'6e51f81f-98a0-4cfc-ba08-15a57107d5ff', 1, 300000)
INSERT [dbo].[OrderDetails] ([OrderDetailID], [OrderID], [ProductID], [Quantity], [Price]) VALUES (N'f46dab72-8889-47ab-b057-c9d101cd8a99', N'd6fde812-817a-419b-854f-a4e8945c3c04', N'a2ab3e02-635b-4706-9b66-d9a7a32adcc5', 2, 59980000)
GO
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'25f7c889-e1e6-4b61-b0ef-3b2e9221151e', N'f7134c7d-37f3-4334-a833-dca2e57c9c8b', CAST(N'2024-12-19T08:53:22.120' AS DateTime), CAST(300000.00 AS Decimal(18, 2)), N'Đang xử lý')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'292417b0-a104-4fd9-80a0-823fbb061097', N'fe5301cd-5c8d-45c7-97bb-8b31516c8a96', CAST(N'2024-12-18T14:51:38.910' AS DateTime), CAST(300000.00 AS Decimal(18, 2)), N'Đang xử lý')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'76c60abf-3a36-4680-8979-a73d80b2af4f', N'f7134c7d-37f3-4334-a833-dca2e57c9c8b', CAST(N'2024-12-19T08:41:24.903' AS DateTime), CAST(24450000.00 AS Decimal(18, 2)), N'Đang xử lý')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'903ab253-ec01-45d9-a23b-5cd8fe285a0f', N'fe5301cd-5c8d-45c7-97bb-8b31516c8a96', CAST(N'2024-12-18T00:00:55.000' AS DateTime), CAST(20300000.00 AS Decimal(18, 2)), N'Đang xử lý')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'b4a74610-cd48-4f55-902d-197fb404179e', N'fe5301cd-5c8d-45c7-97bb-8b31516c8a96', CAST(N'2024-12-18T14:43:13.310' AS DateTime), CAST(20000000.00 AS Decimal(18, 2)), N'Đã huỷ')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'b64288ae-f3d2-4134-ad1b-bb370c5bac5c', N'8946d0de-525e-4aac-a4c2-d60f6fe7455b', CAST(N'2024-12-03T00:36:31.173' AS DateTime), CAST(80300000.00 AS Decimal(18, 2)), N'Đã huỷ')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'c3b85fef-921d-4253-a9b0-8d1ad34f50ce', N'8946d0de-525e-4aac-a4c2-d60f6fe7455b', CAST(N'2024-12-05T22:23:58.123' AS DateTime), CAST(200300000.00 AS Decimal(18, 2)), N'Đang xử lý')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'd6fde812-817a-419b-854f-a4e8945c3c04', N'fe5301cd-5c8d-45c7-97bb-8b31516c8a96', CAST(N'2024-12-18T22:55:48.310' AS DateTime), CAST(64270000.00 AS Decimal(18, 2)), N'Đang xử lý')
INSERT [dbo].[Orders] ([OrderID], [UserID], [OrderDate], [TotalPrice], [Status]) VALUES (N'f39537c3-acf6-4cc2-b579-c1828461b36d', N'fe5301cd-5c8d-45c7-97bb-8b31516c8a96', CAST(N'2024-12-18T22:18:19.383' AS DateTime), CAST(24450000.00 AS Decimal(18, 2)), N'Đã xử lý')
GO
INSERT [dbo].[ProductBrand] ([BrandID], [CatalogueID], [BrandName]) VALUES (N'23749d61-626d-4739-b4f6-7da87202ef04', N'bd0812a1-7df3-476c-b851-fa9595edfe12', N'Intel')
INSERT [dbo].[ProductBrand] ([BrandID], [CatalogueID], [BrandName]) VALUES (N'339f9854-9af2-4203-99cc-2dbc44325aef', N'2fe4a75f-5df8-4f0b-9d38-e291d827e787', N'Canon')
INSERT [dbo].[ProductBrand] ([BrandID], [CatalogueID], [BrandName]) VALUES (N'6de2f729-c7b9-45f7-93d4-e8c88fb3331e', N'991b86f4-f0d5-4d34-b32a-2d2e011e4cf9', N'Marshall')
INSERT [dbo].[ProductBrand] ([BrandID], [CatalogueID], [BrandName]) VALUES (N'856b3aab-b0cb-476a-aeed-fea817ae1be7', N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'Xiaomi')
INSERT [dbo].[ProductBrand] ([BrandID], [CatalogueID], [BrandName]) VALUES (N'bb371d9b-2407-496b-8d5b-d9e148cd67d4', N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'Apple')
INSERT [dbo].[ProductBrand] ([BrandID], [CatalogueID], [BrandName]) VALUES (N'f8db5554-d6b4-4f75-9030-ce47c33f2949', N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'Samsung')
GO
INSERT [dbo].[ProductCatalogues] ([CatalogueID], [CatalogueName]) VALUES (N'2fe4a75f-5df8-4f0b-9d38-e291d827e787', N'Máy ảnh ')
INSERT [dbo].[ProductCatalogues] ([CatalogueID], [CatalogueName]) VALUES (N'991b86f4-f0d5-4d34-b32a-2d2e011e4cf9', N'Loa đài')
INSERT [dbo].[ProductCatalogues] ([CatalogueID], [CatalogueName]) VALUES (N'bd0812a1-7df3-476c-b851-fa9595edfe12', N'Linh kiện điện tử')
INSERT [dbo].[ProductCatalogues] ([CatalogueID], [CatalogueName]) VALUES (N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'Điện Thoại')
GO
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'409b5469-d3d5-4a8e-b08e-14c94a3ec7d1', N'Máy Ảnh Canon EOS 850D', 24450000, N'Máy ảnh tốt', 3, N'/Images/may-anh-canon-eos-850d-kit-ef-s18-55mm-f4-56-is-stm.jpg', N'Màu đen', N'', N'2fe4a75f-5df8-4f0b-9d38-e291d827e787', N'339f9854-9af2-4203-99cc-2dbc44325aef')
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'6e51f81f-98a0-4cfc-ba08-15a57107d5ff', N'Iphone 15', 300000, N'Sản phẩm làm bởi Apple', 23, N'/Images/galaxy-note-3.jpg', N'Đỏ', N'Bé', N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'bb371d9b-2407-496b-8d5b-d9e148cd67d4')
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'a2ab3e02-635b-4706-9b66-d9a7a32adcc5', N'Samsung Galaxy S24 Ultra', 29990000, N'Phần cứng mạnh mẽ đáp ứng tốc độ AI, Làm từ Titan. Cứng cáp bậc nhất bất chấp mọi thử thách, Siêu phân giải 200MP sắc nét và chân thực', 8, N'/Images/2_52709.jpg', N'Xám', N'256gb', N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'f8db5554-d6b4-4f75-9030-ce47c33f2949')
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'a63144ed-f659-42f4-ada6-b98b6d4c0803', N'LOA MARSHALL STANMORE III', 4290000, N'Loa Bluetooth Marshall Kilburn 2 thiết kế cổ điển. Sạc 20 phút sạc 3h. Thân loa chống nước. Đa tính năng. Kết nối Bluetooth aptx 5.0 hiện đại.', 4, N'/Images/1716973356_loa-marshall-stanmore-iii---mau-nau.2.jpg', N'MÀU NÂU', N'', N'991b86f4-f0d5-4d34-b32a-2d2e011e4cf9', N'6de2f729-c7b9-45f7-93d4-e8c88fb3331e')
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'a900ff0f-cb1a-4b75-8304-f2a33599f38a', N'Điện thoại Xiaomi 14 Ultra', 24450000, N'Xiaomi trang bị cho màn hình 14 Ultra các thông số vô cùng ấn tượng là điểm nhấn của chiếc điện thoại này. Với công nghệ LTPO AMOLED, màn hình mang đến khả năng hiển thị 68 tỷ màu.', 5, N'/Images/14-ultra-trang_9d9b62b4a6394c7ea0f13ce518aa784e.jpg', N'Màu đen', N'256gb', N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'856b3aab-b0cb-476a-aeed-fea817ae1be7')
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'b7826f50-9b2d-4e0c-ba6a-f9d4625654a0', N'Ram 5.5Gb', 2200000, N'ram đẹp', 6, N'/Images/ck3109742-cac-loai-ram-may-tinh-1.jpg', N'đen', N'5.5gb', N'bd0812a1-7df3-476c-b851-fa9595edfe12', N'23749d61-626d-4739-b4f6-7da87202ef04')
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'ddeb97b2-f1dc-4191-a36f-12eb54259374', N'Iphone 16 Promax', 20000000, N'Là một dòng sản phẩm của Iphone 16 Series', 8, N'/Images/OIP.jpg', N'Đen', N'256gb', N'e65c3d30-a5cb-4729-8917-4b4aaf4cdf34', N'bb371d9b-2407-496b-8d5b-d9e148cd67d4')
INSERT [dbo].[Products] ([ProductID], [Name], [Price], [Description], [Quantity], [Image_path], [color], [size], [CatalogueID], [BrandID]) VALUES (N'f9722d46-d72b-4b51-b49e-48b5654327df', N'Loa Bluetooth Marshall Middleton', 8090000, N'Loa Marshall Middleton thiết kế nhỏ gọn, âm thanh mạnh mẽ 60W khuấy động mọi không gian, thời lượng sử dụng pin 20h chỉ mất 4.5h sạc đầy. Chống nước ', 5, N'/Images/loa-bluetooth-marshall-middleton-den-1-750x500.jpg', N'Màu đen', N'', N'991b86f4-f0d5-4d34-b32a-2d2e011e4cf9', N'6de2f729-c7b9-45f7-93d4-e8c88fb3331e')
GO
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (0, N'Customer')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (1, N'Admin')
GO
INSERT [dbo].[Users] ([UserID], [Account], [Password], [Name], [RoleID], [PhoneNumber], [Address], [Email]) VALUES (N'49908112-4d21-4ef0-aa2b-72a84d90b628', N'abc', N'6b86b273ff34fce19d6b804eff5a3f5747ada4eaa22f1d49c01e52ddb7875b4b', N'long', 1, N'0386404269', N'Ha Noi', N'ngu')
INSERT [dbo].[Users] ([UserID], [Account], [Password], [Name], [RoleID], [PhoneNumber], [Address], [Email]) VALUES (N'70a7e9ed-817d-48c5-96f0-42ddb01c32bc', N'abc1', N'6b86b273ff34fce19d6b804eff5a3f5747ada4eaa22f1d49c01e52ddb7875b4b', N'long', 1, N'0386404269', N'Ha Noi', N'ngu')
INSERT [dbo].[Users] ([UserID], [Account], [Password], [Name], [RoleID], [PhoneNumber], [Address], [Email]) VALUES (N'7c7ebfcf-f1ff-4851-85d8-24bdc0ba9b5b', N'longta2004', N'6b86b273ff34fce19d6b804eff5a3f5747ada4eaa22f1d49c01e52ddb7875b4b', N'Tạ Văn Long', 1, N'0386404269', N'Hà Nội', N'longta2004.vtv3@gmail.com')
INSERT [dbo].[Users] ([UserID], [Account], [Password], [Name], [RoleID], [PhoneNumber], [Address], [Email]) VALUES (N'8946d0de-525e-4aac-a4c2-d60f6fe7455b', N'aegold', N'a665a45920422f9d417e4867efdc4fb8a04a1f3fff1fa07e998e86f7f7a27ae3', N'Trung', 0, N'0806978', N'âdasd', N'af@gmail.com')
INSERT [dbo].[Users] ([UserID], [Account], [Password], [Name], [RoleID], [PhoneNumber], [Address], [Email]) VALUES (N'f7134c7d-37f3-4334-a833-dca2e57c9c8b', N'gunvno', N'6b86b273ff34fce19d6b804eff5a3f5747ada4eaa22f1d49c01e52ddb7875b4b', N'Long', 0, N'0386404269', N'Ha Noi', N'gunvno2214@gmail.com')
INSERT [dbo].[Users] ([UserID], [Account], [Password], [Name], [RoleID], [PhoneNumber], [Address], [Email]) VALUES (N'fe5301cd-5c8d-45c7-97bb-8b31516c8a96', N'ngu', N'6b86b273ff34fce19d6b804eff5a3f5747ada4eaa22f1d49c01e52ddb7875b4b', N'Ngu', 0, N'0386404269', N'Ha Noi', N'gunvno2214@gmail.com')
GO
ALTER TABLE [dbo].[Cart] ADD  DEFAULT (getdate()) FOR [CreateDate]
GO
ALTER TABLE [dbo].[Cart]  WITH CHECK ADD FOREIGN KEY([ProductID])
REFERENCES [dbo].[Products] ([ProductID])
GO
ALTER TABLE [dbo].[Cart]  WITH CHECK ADD FOREIGN KEY([ProductID])
REFERENCES [dbo].[Products] ([ProductID])
GO
ALTER TABLE [dbo].[Cart]  WITH CHECK ADD FOREIGN KEY([SessionID])
REFERENCES [dbo].[Sessions] ([SessionID])
GO
ALTER TABLE [dbo].[Cart]  WITH CHECK ADD FOREIGN KEY([SessionID])
REFERENCES [dbo].[Sessions] ([SessionID])
GO
ALTER TABLE [dbo].[OrderDetails]  WITH CHECK ADD FOREIGN KEY([ProductID])
REFERENCES [dbo].[Products] ([ProductID])
GO
ALTER TABLE [dbo].[OrderDetails]  WITH CHECK ADD  CONSTRAINT [FK_OrderDeta_Order_76969D2E] FOREIGN KEY([OrderID])
REFERENCES [dbo].[Orders] ([OrderID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[OrderDetails] CHECK CONSTRAINT [FK_OrderDeta_Order_76969D2E]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[Products]  WITH NOCHECK ADD FOREIGN KEY([CatalogueID])
REFERENCES [dbo].[ProductCatalogues] ([CatalogueID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[Products]  WITH CHECK ADD  CONSTRAINT [FK_Products_Brand] FOREIGN KEY([BrandID])
REFERENCES [dbo].[ProductBrand] ([BrandID])
GO
ALTER TABLE [dbo].[Products] CHECK CONSTRAINT [FK_Products_Brand]
GO
ALTER TABLE [dbo].[Sessions]  WITH CHECK ADD FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[Sessions]  WITH CHECK ADD FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[Users]  WITH CHECK ADD FOREIGN KEY([RoleID])
REFERENCES [dbo].[Roles] ([RoleID])
GO
ALTER TABLE [dbo].[Users]  WITH CHECK ADD FOREIGN KEY([RoleID])
REFERENCES [dbo].[Roles] ([RoleID])
GO
ALTER TABLE [dbo].[Variants]  WITH CHECK ADD FOREIGN KEY([ProductID])
REFERENCES [dbo].[Products] ([ProductID])
GO
ALTER TABLE [dbo].[Variants]  WITH CHECK ADD FOREIGN KEY([ProductID])
REFERENCES [dbo].[Products] ([ProductID])
GO
USE [master]
GO
ALTER DATABASE [MobileShopDB_2] SET  READ_WRITE 
GO
