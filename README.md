# narathiwat-rainfall-database
# 🌧️ Narathiwat Rainfall Database Management
**Project:** Data Warehouse Design and CRUD Operations for Rainfall Data in Narathiwat Province
**Role:** Data Scientist / Data Engineer

## 📖 About The Project (เกี่ยวกับโปรเจกต์)
โปรเจกต์นี้เป็นการออกแบบและพัฒนาระบบฐานข้อมูลเชิงสัมพันธ์ (Relational Database) เพื่อจัดการข้อมูลปริมาณน้ำฝนของจังหวัดนราธิวาส โดยนำข้อมูลดิบจากไฟล์ Excel ที่มีความซ้ำซ้อน มาผ่านกระบวนการ **Normalization จนถึงระดับ 3NF** เพื่อสร้างเป็น Data Warehouse ขนาดย่อมที่พร้อมสำหรับการนำไปวิเคราะห์ต่อ (Data Analytics) และใช้เป็นฐานข้อมูลสำหรับโมเดลพยากรณ์ระดับน้ำ (Machine Learning)

## 🛠️ Tech Stack (เครื่องมือที่ใช้)
* **Database:** PostgreSQL
* **Tool:** pgAdmin 4
* **Language:** SQL

## 📊 Database Architecture (สถาปัตยกรรมข้อมูล)
โครงสร้างฐานข้อมูลประกอบด้วย 4 ตารางหลัก ได้แก่:
1. `dim_district` (Dimension: ข้อมูลอำเภอ)
2. `dim_rain_criteria` (Dimension: เกณฑ์วัดระดับน้ำฝน)
3. `fact_daily_rainfall` (Fact: ข้อมูลปริมาณฝนรายวัน)
4. `fact_monthly_summary` (Fact: ข้อมูลสรุปผลรายเดือน)

![ER Diagram](images/ใส่ชื่อไฟล์รูปERDของหนูตรงนี้.png)
*ความสัมพันธ์ใน ER Diagram แสดงการเชื่อมโยงแบบ One-to-Many และการใช้เทคนิค Range Join สำหรับเกณฑ์น้ำฝน*

## 💡 Key Features (จุดเด่นของโปรเจกต์)
* **Normalization (1NF - 3NF):** แก้ปัญหา Repeating Group, Non-atomic value และ Mixed Entity จากไฟล์ข้อมูลดิบ
* **Data Integrity:** มีการตั้งค่า Composite Primary Key เพื่อป้องกันข้อมูลซ้ำซ้อน
* **CRUD Operations:** จำลองสถานการณ์การใช้งานจริงของระบบ
  - **Create:** บันทึกข้อมูลฝนตกรายวัน
  - **Read:** ดึงรายงานและจัดระดับฝนตกอัตโนมัติด้วย Range Join
  - **Update:** แก้ไขข้อผิดพลาดของข้อมูล (Data Cleansing)
  - **Delete:** ล้างข้อมูลยอดสรุปเก่าเพื่อประมวลผลใหม่

## 🚀 How to Run (วิธีรันโค้ด)
1. ติดตั้ง PostgreSQL และ pgAdmin
2. รันสคริปต์ `01_create_schema.sql` ในโฟลเดอร์ `sql_scripts/` เพื่อสร้างตาราง
3. รันสคริปต์ `02_crud_operations.sql` เพื่อทดสอบการทำงานของระบบ
