---
title: Java Collections Framework
date: 2024-12-27
author: Void
description: 
tags:
  - Giới Thiệu
  - Sử Dụng
---

## **Giới thiệu về Java Collections Framework**
Java Collections Framework (JCF) là một tập hợp các lớp và giao diện trong Java, cung cấp các cấu trúc dữ liệu và thuật toán để quản lý các tập hợp đối tượng. Dưới đây là cái nhìn tổng quan về JCF:

---

## **1. Các Giao Diện Chính**
Collection: Giao diện cơ sở cho tất cả các tập hợp. Nó định nghĩa các phương thức cơ bản như thêm, xóa, và kiểm tra sự tồn tại của phần tử.
List: Một tập hợp các phần tử có thứ tự, cho phép các phần tử trùng lặp. Ví dụ: ArrayList, LinkedList.
Set: Một tập hợp không cho phép các phần tử trùng lặp. Ví dụ: HashSet, TreeSet.
Map: Cấu trúc lưu trữ các cặp key-value, không cho phép key trùng lặp. Ví dụ: HashMap, TreeMap.

---

## **2. Các Lớp Cụ Thể**
ArrayList: Danh sách động dựa trên mảng, cho phép truy cập nhanh đến các phần tử nhưng chi phí cao khi thêm/xóa phần tử giữa danh sách.
LinkedList: Danh sách liên kết cho phép thêm/xóa phần tử nhanh hơn so với ArrayList, nhưng truy cập phần tử chậm hơn.
HashSet: Tập hợp không cho phép trùng lặp, sử dụng bảng băm để lưu trữ, cho phép truy cập nhanh.
TreeSet: Tập hợp không trùng lặp, sắp xếp theo thứ tự tự nhiên hoặc theo một comparator.
HashMap: Bảng băm cho phép lưu trữ cặp key-value, cho phép truy cập nhanh đến các giá trị dựa trên key.
TreeMap: Bảng băm sắp xếp theo thứ tự tự nhiên hoặc theo một comparator.

---

## **3. Thuật Toán**
JCF cung cấp các thuật toán cho các hoạt động như tìm kiếm, sắp xếp, và lặp qua các tập hợp thông qua lớp Collections.

---

## **4. Ưu Điểm của Java Collections Framework**
Tính mở rộng: Dễ dàng mở rộng và tùy chỉnh các tập hợp.
Tính đồng nhất: Cung cấp một cách tiếp cận đồng nhất để làm việc với các tập hợp khác nhau.
Hiệu suất: Được thiết kế để tối ưu hóa hiệu suất cho các thao tác trên tập hợp.
Dễ sử dụng: Cung cấp nhiều phương thức tiện ích để thao tác với các tập hợp.

---

## **5. Sử Dụng JCF**
Bạn có thể sử dụng JCF bằng cách import các lớp và giao diện tương ứng. Ví dụ:


import java.util.ArrayList;

import java.util.HashMap;

import java.util.HashSet;

import java.util.List;

import java.util.Map;

import java.util.Set;


// Sử dụng ArrayList

List<String> list = new ArrayList<>();

list.add("Hello");

list.add("World");

// Sử dụng HashSet

Set<String> set = new HashSet<>();

set.add("Java");

set.add("Java"); // Không thêm được vì trùng lặp

// Sử dụng HashMap

Map<String, Integer> map = new HashMap<>();

map.put("Alice", 30);

map.put("Bob", 25);