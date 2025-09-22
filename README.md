<img width="756" height="229" alt="Categories-part2" src="https://github.com/user-attachments/assets/fda01240-df2c-4ca7-a54d-b4a3b0194bf9" />
<img width="711" height="227" alt="user-part2" src="https://github.com/user-attachments/assets/ef008dca-4cf0-4e67-afa1-ea9027001beb" />
<img width="534" height="106" alt="Updatethestock-part5" src="https://github.com/user-attachments/assets/9c962126-7f22-4db2-a556-17b36b972159" />
<img width="1019" height="253" alt="top-sellingproduct-part4" src="https://github.com/user-attachments/assets/c9133abc-a4dd-4319-8165-075bcaf22dd7" />
<img width="1074" height="371" alt="Showeachorder-part4" src="https://github.com/user-attachments/assets/d0dc887b-c1f4-4e45-9829-f4709608a23c" />
<img width="1100" height="464" alt="Showallorderdetails-part4" src="https://github.com/user-attachments/assets/34817966-7b4f-4481-9be1-12d90f5b6eb1" />
<img width="1009" height="573" alt="Show all products-part3" src="https://github.com/user-attachments/assets/dade728c-e067-4623-b0b0-9b003aa9a6d8" />
<img width="1111" height="344" alt="Retrieveallorders-part3" src="https://github.com/user-attachments/assets/2c381339-b00b-4add-88fc-c3a459d7d4e3" />
<img width="898" height="353" alt="Products-part2" src="https://github.com/user-attachments/assets/d41b44a4-0d04-4fa6-a34f-3e6049b37c08" />
<img width="564" height="175" alt="Orders-part2" src="https://github.com/user-attachments/assets/46419f2b-7f82-4c83-aece-5a707cedc62d" />
<img width="832" height="361" alt="Listallproducts-part3" src="https://github.com/user-attachments/assets/833344f8-16fb-43c5-a17e-1bbe283b7f8a" />
<img width="1122" height="440" alt="Displaythenumber-part4" src="https://github.com/user-attachments/assets/5cf330f7-bd53-4a42-a7df-78d45f1e6485" />
<img width="572" height="148" alt="Deleteproduct-part5" src="https://github.com/user-attachments/assets/0865055a-e135-4709-bf6f-7b2101de565d" />
<img width="511" height="111" alt="Changethestatus-part5" src="https://github.com/user-attachments/assets/90b4dbf6-1a0a-43c7-aad4-07e61720fa4f" />
[e_commerce.sql](https://github.com/user-attachments/files/22472661/e_commerce.sql)
-- phpMyAdmin SQL Dump
-- version 5.2.1
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Generation Time: Sep 22, 2025 at 07:29 PM
-- Server version: 10.4.32-MariaDB
-- PHP Version: 8.0.30

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `e/commerce`
--

-- --------------------------------------------------------

--
-- Table structure for table `categories`
--

CREATE TABLE `categories` (
  `category_id` int(11) NOT NULL,
  `name` varchar(100) NOT NULL,
  `description` text DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data for table `categories`
--

INSERT INTO `categories` (`category_id`, `name`, `description`) VALUES
(1, 'Electronics', 'Electronic devices like computers, phones, and accessories'),
(2, 'Clothing', 'children clothing items'),
(3, 'Health', 'Medical tools');

-- --------------------------------------------------------

--
-- Table structure for table `orderitems`
--

CREATE TABLE `orderitems` (
  `order_item_id` int(11) NOT NULL,
  `order_id` int(11) DEFAULT NULL,
  `product_id` int(11) DEFAULT NULL,
  `quantity` int(11) NOT NULL,
  `price` decimal(10,2) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data for table `orderitems`
--

INSERT INTO `orderitems` (`order_item_id`, `order_id`, `product_id`, `quantity`, `price`) VALUES
(1, 1, 1, 1, 990.00),
(2, 1, 2, 2, 20.00),
(3, 2, 4, 3, 25.00),
(5, 3, 7, 5, 2.00),
(6, 3, 8, 2, 1.00),
(7, 4, 3, 1, 305.00),
(8, 4, 6, 1, 150.00),
(9, 5, 9, 2, 305.00),
(10, 5, 10, 1, 555.00);

-- --------------------------------------------------------

--
-- Table structure for table `orders`
--

CREATE TABLE `orders` (
  `order_id` int(11) NOT NULL,
  `user_id` int(11) DEFAULT NULL,
  `order_date` timestamp NOT NULL DEFAULT current_timestamp(),
  `status` enum('Pending','Shipped','Delivered') DEFAULT 'Pending'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data for table `orders`
--

INSERT INTO `orders` (`order_id`, `user_id`, `order_date`, `status`) VALUES
(1, 1, '2025-09-12 21:00:00', 'Pending'),
(2, 2, '2025-09-10 21:00:00', 'Shipped'),
(3, 3, '2025-09-01 21:00:00', 'Shipped'),
(4, 1, '2025-09-08 21:00:00', 'Pending'),
(5, 4, '2025-08-31 21:00:00', 'Shipped');

-- --------------------------------------------------------

--
-- Table structure for table `products`
--

CREATE TABLE `products` (
  `product_id` int(11) NOT NULL,
  `name` varchar(150) NOT NULL,
  `description` text DEFAULT NULL,
  `price` decimal(10,2) NOT NULL,
  `stock` int(11) NOT NULL,
  `category_id` int(11) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data for table `products`
--

INSERT INTO `products` (`product_id`, `name`, `description`, `price`, `stock`, `category_id`, `created_at`) VALUES
(1, 'Laptop', 'High performance laptop', 990.00, 8, 1, '2025-09-22 16:17:17'),
(2, 'Mouse', 'Wireless mouse', 20.00, 50, 1, '2025-09-22 16:17:17'),
(3, 'Keyboard', ' keyboard', 50.00, 30, 1, '2025-09-22 16:17:17'),
(4, 'Shirt', 'Cotton t-shirt for children', 25.00, 100, 2, '2025-09-22 16:17:17'),
(5, 'Jeans', 'red jeans', 40.00, 60, 2, '2025-09-22 16:17:17'),
(6, 'Jacket', ' jacket', 60.00, 40, 2, '2025-09-22 16:17:17'),
(7, 'Thermometer', 'Thermometer', 255.00, 300, 3, '2025-09-22 16:17:17'),
(8, 'Medical bed', 'Medical bed', 150.00, 20, 3, '2025-09-22 16:17:17'),
(9, 'Stethoscope', 'Stethoscope', 305.00, 10, 3, '2025-09-22 16:17:17'),
(10, 'Otoscope', 'Otoscope', 555.00, 90, 3, '2025-09-22 16:17:17');

-- --------------------------------------------------------

--
-- Table structure for table `users`
--

CREATE TABLE `users` (
  `user_id` int(11) NOT NULL,
  `name` varchar(100) NOT NULL,
  `email` varchar(150) NOT NULL,
  `password` varchar(255) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data for table `users`
--

INSERT INTO `users` (`user_id`, `name`, `email`, `password`, `created_at`) VALUES
(1, 'lana', 'lana2001@gamil.com', '123456', '2025-09-22 15:57:25'),
(2, 'mousa', 'mousa1980@gamil.com', 'abcdef', '2025-09-22 15:57:25'),
(3, 'Khaled', 'khaled22@gamil.com', 'qwerty', '2025-09-22 15:57:25'),
(4, 'rana', 'rana2000@gamil.com', 'password1', '2025-09-22 15:57:25'),
(5, 'lina', 'lina2005@gamil.com', 'pass123', '2025-09-22 15:57:25');

--
-- Indexes for dumped tables
--

--
-- Indexes for table `categories`
--
ALTER TABLE `categories`
  ADD PRIMARY KEY (`category_id`);

--
-- Indexes for table `orderitems`
--
ALTER TABLE `orderitems`
  ADD PRIMARY KEY (`order_item_id`),
  ADD KEY `order_id` (`order_id`),
  ADD KEY `product_id` (`product_id`);

--
-- Indexes for table `orders`
--
ALTER TABLE `orders`
  ADD PRIMARY KEY (`order_id`),
  ADD KEY `user_id` (`user_id`);

--
-- Indexes for table `products`
--
ALTER TABLE `products`
  ADD PRIMARY KEY (`product_id`),
  ADD KEY `category_id` (`category_id`);

--
-- Indexes for table `users`
--
ALTER TABLE `users`
  ADD PRIMARY KEY (`user_id`),
  ADD UNIQUE KEY `email` (`email`);

--
-- AUTO_INCREMENT for dumped tables
--

--
-- AUTO_INCREMENT for table `categories`
--
ALTER TABLE `categories`
  MODIFY `category_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT for table `orderitems`
--
ALTER TABLE `orderitems`
  MODIFY `order_item_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=11;

--
-- AUTO_INCREMENT for table `orders`
--
ALTER TABLE `orders`
  MODIFY `order_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT for table `products`
--
ALTER TABLE `products`
  MODIFY `product_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=11;

--
-- AUTO_INCREMENT for table `users`
--
ALTER TABLE `users`
  MODIFY `user_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- Constraints for dumped tables
--

--
-- Constraints for table `orderitems`
--
ALTER TABLE `orderitems`
  ADD CONSTRAINT `orderitems_ibfk_1` FOREIGN KEY (`order_id`) REFERENCES `orders` (`order_id`),
  ADD CONSTRAINT `orderitems_ibfk_2` FOREIGN KEY (`product_id`) REFERENCES `products` (`product_id`);

--
-- Constraints for table `orders`
--
ALTER TABLE `orders`
  ADD CONSTRAINT `orders_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `users` (`user_id`);

--
-- Constraints for table `products`
--
ALTER TABLE `products`
  ADD CONSTRAINT `products_ibfk_1` FOREIGN KEY (`category_id`) REFERENCES `categories` (`category_id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
