---
title: Lập Trình Đa Luồng
date: 2024-12-27
author: Void
description: Lập trình Java từ cơ bản đến nâng cao
tags:
  - Giới Thiệu
  - Quản Lý
  - Vấn Đề
---

## **Giới thiệu lập trình đa luồng**
Lập trình đa luồng (Multithreading) trong Java cho phép thực hiện nhiều luồng (threads) song song, giúp tối ưu hóa hiệu suất ứng dụng và cải thiện khả năng phản hồi. Dưới đây là cái nhìn tổng quan về lập trình đa luồng trong Java:

---

## **1. Khái Niệm Cơ Bản**
Luồng (Thread): Là một đơn vị thực thi độc lập trong một chương trình. Mỗi luồng có thể thực hiện một nhiệm vụ riêng mà không ảnh hưởng đến các luồng khác.
Đa luồng: Là khả năng chạy nhiều luồng đồng thời trong cùng một ứng dụng.

---

## **2. Tại Sao Sử Dụng Đa Luồng?**
Tăng hiệu suất: Lợi dụng tài nguyên CPU, thực hiện nhiều tác vụ cùng một lúc.
Cải thiện khả năng phản hồi: Ứng dụng có thể thực hiện các tác vụ nền mà không làm treo giao diện người dùng.
Quản lý tác vụ đồng thời: Thích hợp cho ứng dụng yêu cầu xử lý đồng thời, như máy chủ web, trò chơi, hoặc ứng dụng xử lý dữ liệu lớn.

---

## **3. Cách Tạo Luồng**
Có hai cách chính để tạo luồng trong Java:

a. Kế thừa lớp Thread

class MyThread extends Thread {

    public void run() {

        System.out.println("Luồng đang chạy: " + Thread.currentThread().getName());

    }

}

// Sử dụng luồng

MyThread thread1 = new MyThread();

thread1.start();

b. Thực hiện giao diện Runnable

class MyRunnable implements Runnable {

    public void run() {

        System.out.println("Luồng đang chạy: " + Thread.currentThread().getName());

    }

}

// Sử dụng luồng

Thread thread2 = new Thread(new MyRunnable());

thread2.start();

---

## **4. Quản Lý Luồng**
Phương thức start(): Bắt đầu luồng, gọi phương thức run() của luồng.
Phương thức sleep(long millis): Dừng luồng trong khoảng thời gian nhất định.
Phương thức join(): Chờ cho luồng khác hoàn thành trước khi tiếp tục.
Phương thức yield(): Tạm dừng luồng hiện tại và cho phép luồng khác thực thi.

---

## **5. Vấn Đề Đồng Bộ (Synchronization)**
Khi nhiều luồng cùng truy cập vào dữ liệu chung, có thể xảy ra tình trạng tranh chấp (race condition). Để tránh điều này, Java cung cấp các công cụ đồng bộ hóa:

Synchronized Methods: Bảo vệ toàn bộ phương thức.

Synchronized Blocks: Bảo vệ một phần cụ thể của mã.

---

## **6. Executor Framework**
Java cung cấp Executor Framework để quản lý luồng dễ dàng hơn:

ThreadPool: Giúp tái sử dụng luồng, tránh việc tạo và hủy luồng liên tục.

ExecutorService: Giao diện cho phép quản lý và điều phối luồng.

ExecutorService executor = Executors.newFixedThreadPool(2);

executor.submit(new MyRunnable());

executor.shutdown();

---

## **7. Các Vấn Đề Thường Gặp**
Deadlock: Tình trạng hai hoặc nhiều luồng chờ nhau vô hạn.

Starvation: Một luồng không bao giờ có cơ hội thực thi vì các luồng khác liên tục chiếm ưu thế.