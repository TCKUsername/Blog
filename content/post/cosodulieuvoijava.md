---
title: Java Với Cơ Sở Dữ Liệu
date: 2024-12-27
author: Void
description: 
tags:
  - Giới Thiệu Công Cụ
---

## **Giới thiệu Java với cơ sở dữ liệu**

Java cung cấp nhiều cách để tương tác với cơ sở dữ liệu, chủ yếu thông qua JDBC (Java Database Connectivity). Dưới đây là cái nhìn tổng quan về cách Java kết nối và làm việc với cơ sở dữ liệu:

---

## **1. Java Database Connectivity (JDBC)

JDBC là một API trong Java cho phép lập trình viên kết nối và thao tác với cơ sở dữ liệu quan hệ. Nó cung cấp các lớp và giao diện để thực hiện các tác vụ như kết nối, truy vấn và cập nhật dữ liệu.

a. Thành phần chính của JDBC
DriverManager: Quản lý danh sách các driver JDBC. Chịu trách nhiệm tạo kết nối đến cơ sở dữ liệu.

Connection: Đại diện cho kết nối đến một cơ sở dữ liệu. Thực hiện các thao tác như tạo Statement, PreparedStatement, v.v.

Statement: Dùng để thực hiện các câu lệnh SQL. Có ba loại:

Statement: Dùng cho câu lệnh SQL tĩnh.

PreparedStatement: Dùng cho câu lệnh SQL động, an toàn hơn với SQL Injection.

CallableStatement: Dùng để gọi các thủ tục (stored procedures).

ResultSet: Đại diện cho tập kết quả của câu lệnh SQL SELECT.

---

## **2. Kết Nối đến Cơ Sở Dữ Liệu

Dưới đây là ví dụ về cách kết nối đến cơ sở dữ liệu MySQL bằng JDBC:

import java.sql.Connection;

import java.sql.DriverManager;

import java.sql.SQLException;

public class DatabaseConnection {

    public static void main(String[] args) {

        String url = "jdbc:mysql://localhost:3306/ten_database"; // Thay thế 'ten_database' bằng tên cơ sở dữ liệu của bạn

        String user = "username"; // Thay thế 'username' bằng tên người dùng của bạn

        String password = "password"; // Thay thế 'password' bằng mật khẩu của bạn

        try {
            Connection connection = DriverManager.getConnection(url, user, password);
            System.out.println("Kết nối thành công!");
            // Thực hiện các thao tác với cơ sở dữ liệu ở đây
            connection.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}

---

## **3. Thực hiện Các Câu Lệnh SQL**

Dưới đây là ví dụ về cách sử dụng Statement và PreparedStatement để thực hiện câu lệnh SQL:

a. Sử dụng Statement

import java.sql.Connection;

import java.sql.DriverManager;

import java.sql.ResultSet;

import java.sql.SQLException;

import java.sql.Statement;

public class ExecuteStatement {

    public static void main(String[] args) {

        // Kết nối như ở ví dụ trước
        try (Connection connection = DriverManager.getConnection(url, user, password);
             Statement statement = connection.createStatement()) {
             
            String sql = "SELECT * FROM users";
            ResultSet resultSet = statement.executeQuery(sql);
            
            while (resultSet.next()) {
                System.out.println("ID: " + resultSet.getInt("id") + ", Tên: " + resultSet.getString("name"));
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}

---

b. Sử dụng PreparedStatement

import java.sql.Connection;

import java.sql.DriverManager;

import java.sql.PreparedStatement;

import java.sql.SQLException;

public class ExecutePreparedStatement {

    public static void main(String[] args) {
        
        String sql = "INSERT INTO users (name, email) VALUES (?, ?)";
        
        try (Connection connection = DriverManager.getConnection(url, user, password);
             PreparedStatement preparedStatement = connection.prepareStatement(sql)) {
             
            preparedStatement.setString(1, "Nguyen Van A");
            preparedStatement.setString(2, "nguyenvana@example.com");
            int rowsAffected = preparedStatement.executeUpdate();
            System.out.println("Số hàng bị ảnh hưởng: " + rowsAffected);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}