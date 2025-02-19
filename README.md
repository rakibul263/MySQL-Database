<h1 align="center" style="color: skyblue;">All About MySQL</h1>


### **`CREATE TABLE` কিভাবে কাজ করে?**  
SQL-এ `CREATE TABLE` ব্যবহার করা হয় **একটি নতুন টেবিল তৈরি করতে**।  

---

## **✅ `CREATE TABLE` এর সাধারণ গঠন (Syntax)**  
```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    column3 datatype constraints,
    ...
);
```
🔹 **`table_name`** → নতুন টেবিলের নাম  
🔹 **`column1, column2, ...`** → কলামের নাম  
🔹 **`datatype`** → কলামের জন্য ডাটা টাইপ (যেমন: `INT`, `VARCHAR`, `DATE`, `DECIMAL` ইত্যাদি)  
🔹 **`constraints`** → কলামের রুল (যেমন: `PRIMARY KEY`, `NOT NULL`, `UNIQUE` ইত্যাদি)  

---

## **✅ `employees` টেবিল তৈরি করা**  
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT, 
    name VARCHAR(50) NOT NULL,
    department VARCHAR(30),
    age INT CHECK (age >= 18),
    salary DECIMAL(10,2),
    join_date DATE
);
```
🔹 **`id`** → Primary Key (স্বয়ংক্রিয়ভাবে ১, ২, ৩... হবে)  
🔹 **`name`** → নাম (`VARCHAR(50)`, খালি রাখা যাবে না)  
🔹 **`department`** → বিভাগ (`VARCHAR(30)`, খালি রাখা যাবে)  
🔹 **`age`** → বয়স (কমপক্ষে ১৮ হতে হবে)  
🔹 **`salary`** → বেতন (`DECIMAL(10,2)` অর্থাৎ, ১০ ডিজিটের মধ্যে ২ ডিজিট দশমিকের পর)  
🔹 **`join_date`** → যোগদানের তারিখ  

---

## **✅ `CREATE TABLE`-এর সাথে কন্ডিশন ব্যবহার করা**
### **১. যদি টেবিলটি আগে থেকেই থাকে, তাহলে ডিলিট করে নতুন করে তৈরি করবে**  
```sql
DROP TABLE IF EXISTS employees;
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    department VARCHAR(30),
    age INT CHECK (age >= 18),
    salary DECIMAL(10,2),
    join_date DATE
);
```
🔹 **`DROP TABLE IF EXISTS employees;`** → যদি `employees` টেবিল আগে থাকে, তাহলে মুছে ফেলে নতুন করে তৈরি করবে  

---

### **২. যদি টেবিলটি আগে থেকে না থাকে, তাহলে নতুন তৈরি করবে**  
```sql
CREATE TABLE IF NOT EXISTS employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    department VARCHAR(30),
    age INT CHECK (age >= 18),
    salary DECIMAL(10,2),
    join_date DATE
);
```
🔹 **`IF NOT EXISTS`** → যদি `employees` টেবিল না থাকে, তাহলে নতুন করে তৈরি করবে  

---

### **`INSERT INTO` কিভাবে কাজ করে?**  
SQL-এ `INSERT INTO` ব্যবহার করা হয় **টেবিলে নতুন ডাটা সংযুক্ত করতে**।  

---

## **✅ `INSERT INTO` এর সাধারণ গঠন (Syntax)**
```sql
INSERT INTO table_name (column1, column2, column3, ...) 
VALUES (value1, value2, value3, ...);
```
🔹 **`table_name`** → যে টেবিলে ডাটা ইনসার্ট করা হবে  
🔹 **`column1, column2, ...`** → যে কলামগুলোর জন্য ডাটা দেওয়া হবে  
🔹 **`value1, value2, ...`** → যে মানগুলো ইনসার্ট হবে  

---

## **✅ `employees` টেবিলে ২০ জন কর্মীর ডাটা ইনসার্ট করা**  
```sql
INSERT INTO employees (name, department, age, salary, join_date) VALUES
('Samiul', 'IT', 25, 50000.00, '2022-03-15'),
('Fahim', 'HR', 30, 45000.50, '2021-07-10'),
('Ayesha', 'Finance', 28, 55000.75, '2022-10-05'),
('Rifat', 'IT', 27, 48000.00, '2023-01-12'),
('Tanjim', 'Marketing', 29, 47000.00, '2022-06-20'),
('Nabila', 'HR', 26, 42000.00, '2023-04-11'),
('Hasib', 'IT', 31, 52000.50, '2021-09-14'),
('Jannat', 'Finance', 24, 51000.00, '2022-02-07'),
('Rakib', 'IT', 28, 50000.00, '2023-03-18'),
('Mou', 'Marketing', 27, 46000.00, '2022-12-05'),
('Sabbir', 'Finance', 29, 53000.00, '2021-08-25'),
('Raihan', 'HR', 32, 41000.00, '2022-07-17'),
('Shamim', 'IT', 26, 47000.50, '2023-05-21'),
('Jui', 'Marketing', 30, 49000.00, '2022-11-09'),
('Tarek', 'Finance', 28, 52000.00, '2021-06-30'),
('Afia', 'HR', 25, 43000.00, '2023-08-14'),
('Mamun', 'IT', 33, 54000.75, '2022-09-19'),
('Tanvir', 'Marketing', 27, 48000.00, '2023-02-22'),
('Faria', 'Finance', 26, 51000.00, '2022-04-16'),
('Mehedi', 'HR', 29, 45000.00, '2023-07-29');
```
🔹 এখানে **২০ জন কর্মীর তথ্য ইনসার্ট করা হয়েছে**  
🔹 **`id` কলাম `AUTO_INCREMENT` থাকলে** সেটি স্বয়ংক্রিয়ভাবে সংখ্যা অ্যাসাইন করবে  

---

## **✅ সব কলামে ইনসার্ট করা (কোনো নির্দিষ্ট কলাম উল্লেখ না করে)**
```sql
INSERT INTO employees VALUES 
(21, 'Kamal', 'IT', 30, 52000.00, '2023-06-12');
```
🔹 **সব কলামের জন্য মান দিতে হবে**  
🔹 **`id` কলামে স্বয়ংক্রিয় সংখ্যা যুক্ত হলে প্রথম কলাম বাদ দেওয়া উচিত**  

---

## **✅ একাধিক `INSERT` একসাথে চালানো (Bulk Insert)**
```sql
INSERT INTO employees (name, department, age, salary, join_date) VALUES
('Arif', 'IT', 28, 49000.00, '2023-01-05'),
('Mahin', 'Finance', 27, 53000.00, '2022-08-23'),
('Saima', 'HR', 26, 44000.00, '2023-10-10');
```
🔹 **একটি `INSERT INTO` স্টেটমেন্টে একাধিক রো ইনসার্ট করা যায়**  

---

## **✅ `INSERT` + `SELECT` (অন্য টেবিল থেকে ডাটা কপি করা)**  
যদি আমরা **অন্য একটি টেবিল থেকে ডাটা কপি করে `employees` টেবিলে রাখতে চাই**:  
```sql
INSERT INTO employees (name, department, age, salary, join_date)
SELECT full_name, dept, years, pay, start_date FROM old_employees;
```
🔹 এটি **`old_employees` টেবিল থেকে ডাটা নিয়ে `employees` টেবিলে সংযুক্ত করবে**  

---

## **✅ ইনসার্ট করার পর ডাটা চেক করা (`SELECT` দিয়ে)**
```sql
SELECT * FROM employees;
```
🔹 **`employees` টেবিলে নতুন যোগ করা ডাটা দেখাবে**  

---

### **`UPDATE` কিভাবে কাজ করে?**  
SQL-এ `UPDATE` ব্যবহার করা হয় **অবস্থানে থাকা ডাটা পরিবর্তন করতে**।  

---

## **✅ `UPDATE` এর সাধারণ গঠন (Syntax)**  
```sql
UPDATE table_name  
SET column1 = value1, column2 = value2, ...  
WHERE condition;
```

🔹 **`table_name`** → যে টেবিলের ডাটা আপডেট করবেন  
🔹 **`SET`** → যেসব কলামের মান পরিবর্তন করতে চান  
🔹 **`WHERE`** → কোন রো (row) আপডেট হবে, সেটা ঠিক করতে  

⚠️ **IMPORTANT:**  
**`WHERE` না দিলে পুরো টেবিলের ডাটা আপডেট হয়ে যাবে!** সাবধানে ব্যবহার করুন।  

---

## **✅ ১. এক কলাম আপডেট করা**  
ধরি, আমরা **ID ১** নম্বর কর্মীর বেতন বাড়িয়ে **৬০০০০** করতে চাই:  
```sql
UPDATE employees  
SET salary = 60000  
WHERE id = 1;
```

🔹 **Result:** `id = 1` এর **`salary` 60000** এ আপডেট হবে।  

---

## **✅ ২. একাধিক কলাম আপডেট করা**  
যদি আমরা **ID ২** নম্বর কর্মীর **বেতন ও ডিপার্টমেন্ট** পরিবর্তন করতে চাই:  
```sql
UPDATE employees  
SET salary = 48000, department = 'Marketing'  
WHERE id = 2;
```

🔹 **Result:** `id = 2` এর **বেতন** এবং **ডিপার্টমেন্ট** আপডেট হবে।  

---

## **✅ ৩. শর্ত অনুযায়ী আপডেট করা**  
যদি আমরা **যারা IT ডিপার্টমেন্টে আছেন, তাদের বেতন ১০% বাড়াতে চাই**:  
```sql
UPDATE employees  
SET salary = salary * 1.10  
WHERE department = 'IT';
```

🔹 **Result:** **IT ডিপার্টমেন্টের সব কর্মীর বেতন ১০% বাড়বে।**  

---

## **✅ ৪. নির্দিষ্ট তারিখের উপর ভিত্তি করে আপডেট করা**  
যদি আমরা **যারা ২০২২ সালের আগে জয়েন করেছে, তাদের ডিপার্টমেন্ট 'Senior' করতে চাই**:  
```sql
UPDATE employees  
SET department = 'Senior'  
WHERE join_date < '2022-01-01';
```

🔹 **Result:** **২০২২ সালের আগে জয়েন করা কর্মীদের ডিপার্টমেন্ট 'Senior' হবে।**  

---

## **✅ ৫. `UPDATE` করার পর ডাটা চেক করা (`SELECT`)**  
```sql
SELECT * FROM employees;
```

🔹 **আপডেটেড ডাটা দেখানোর জন্য `SELECT` ব্যবহার করতে পারেন।**  

---

## **✅ ৬. `UPDATE` + `LIMIT` (সীমিত রো আপডেট করা)**  
যদি আমরা **শুধু প্রথম ৫ জনের ডিপার্টমেন্ট 'Test' করতে চাই**:  
```sql
UPDATE employees  
SET department = 'Test'  
LIMIT 5;
```

🔹 **Result:** **প্রথম ৫ জন কর্মীর ডিপার্টমেন্ট 'Test' হবে।**  

---

## **✅ ৭. `UPDATE` + `ORDER BY` (সাজিয়ে আপডেট করা)**  
যদি আমরা **সর্বনিম্ন বেতনের কর্মীর বেতন ৪৫০০০ করতে চাই**:  
```sql
UPDATE employees  
SET salary = 45000  
ORDER BY salary ASC  
LIMIT 1;
```

🔹 **Result:** **সবচেয়ে কম বেতন পাওয়া কর্মীর বেতন ৪৫০০০ হবে।**  

---

## **✅ সংক্ষেপে `UPDATE` ব্যবহার করার সুবিধা**  
✔ **ডাটা সহজে পরিবর্তন করা যায়**  
✔ **শর্ত অনুযায়ী নির্দিষ্ট রো আপডেট করা যায়**  
✔ **গাণিতিক অপারেশন (যেমন: `salary * 1.10`) করা যায়**  



### **`WHERE` Clause কি এবং এটি কিভাবে কাজ করে?**  
`WHERE` ক্লজ SQL-তে **শর্ত নির্ধারণের জন্য ব্যবহৃত হয়**। যখন আমরা কোনো টেবিল থেকে **নির্দিষ্ট ডেটা ফিল্টার** করতে চাই, তখন `WHERE` ক্লজ ব্যবহার করা হয়। এটি মূলত `SELECT`, `UPDATE`, `DELETE` এবং `INSERT` স্টেটমেন্টের সাথে ব্যবহার করা হয়।

---

### **উদাহরণ ১: নির্দিষ্ট ডিপার্টমেন্টের কর্মচারীদের খুঁজে বের করা**  
ধরা যাক, আমরা `IT` বিভাগে কর্মরত কর্মচারীদের দেখতে চাই।  

```sql
SELECT * FROM Employees WHERE department = 'IT';
```
👉 এই কিউরিটি `Employees` টেবিল থেকে শুধুমাত্র `IT` বিভাগে কাজ করা কর্মচারীদের তথ্য দেখাবে।

---

### **উদাহরণ ২: ৩০ বছরের বেশি বয়সী কর্মচারীদের তালিকা**  
```sql
SELECT * FROM Employees WHERE age > 30;
```
👉 এই কিউরি সেইসব কর্মচারীদের তথ্য দেখাবে যাদের বয়স **৩০ বছরের বেশি**।

---

### **উদাহরণ ৩: নির্দিষ্ট বেতনসীমার মধ্যে কর্মচারীদের তালিকা**  
ধরি, আমরা এমন কর্মচারীদের দেখতে চাই যাদের বেতন **৪০০০০ থেকে ৫০০০০** এর মধ্যে।  

```sql
SELECT * FROM Employees WHERE salary BETWEEN 40000 AND 50000;
```
👉 এই কিউরি শুধু তাদের দেখাবে যাদের বেতন ৪০০০০ থেকে ৫০০০০ টাকার মধ্যে আছে।

---

### **উদাহরণ ৪: `HR` বিভাগ বাদে অন্যদের তথ্য**  
আমরা যদি `HR` বিভাগের কর্মচারীদের বাদ দিয়ে বাকি সকলকে দেখতে চাই:  

```sql
SELECT * FROM Employees WHERE department <> 'HR';
```
(এখানে `<>` অর্থ **"সমান নয়"**)

---

### **উদাহরণ ৫: ২০২১ সালের পরে যোগ দেওয়া কর্মচারীরা**  
```sql
SELECT * FROM Employees WHERE join_date > '2021-12-31';
```
👉 এই কিউরিটি **২০২২ বা এর পরে** যোগ দেওয়া কর্মচারীদের দেখাবে।

---

### **উদাহরণ ৬: নির্দিষ্ট নামে কর্মচারী খুঁজে বের করা**  
যদি আমরা `Rahim Islam` নামের কর্মচারীর তথ্য জানতে চাই:  
```sql
SELECT * FROM Employees WHERE name = 'Rahim Islam';
```
👉 এটি শুধুমাত্র **Rahim Islam**-এর তথ্য দেখাবে।

---

### **উদাহরণ ৭: একাধিক শর্ত একসাথে ব্যবহার করা (`AND` এবং `OR`)**  

✅ **যদি আমরা `IT` বিভাগের কর্মচারীদের খুঁজতে চাই যাদের বয়স ২৫ বছরের বেশি:**  
```sql
SELECT * FROM Employees WHERE department = 'IT' AND age > 25;
```
👉 এটি শুধু `IT` বিভাগের **যাদের বয়স ২৫ বছরের বেশি** তাদের তথ্য দেখাবে।

✅ **যদি আমরা `HR` বা `Finance` বিভাগের কর্মচারীদের দেখতে চাই:**  
```sql
SELECT * FROM Employees WHERE department = 'HR' OR department = 'Finance';
```
👉 এটি `HR` এবং `Finance` বিভাগে কর্মরত সকল কর্মচারীর তথ্য দেখাবে।

---

### **উপসংহার**  
🔹 `WHERE` ক্লজ **ডাটাবেজ থেকে নির্দিষ্ট ডেটা ফিল্টার করতে সাহায্য করে**।  
🔹 এটি `=`, `>`, `<`, `>=`, `<=`, `<>`, `BETWEEN`, `AND`, `OR` ইত্যাদি অপারেটরের মাধ্যমে কাজ করে।  
🔹 আমরা `WHERE` ব্যবহার করে নির্দিষ্ট বিভাগ, বয়স, বেতন, যোগদানের তারিখ ইত্যাদির ভিত্তিতে কর্মচারীদের খুঁজে বের করতে পারি।



### **`BETWEEN` কিভাবে কাজ করে?**  
`BETWEEN` **দুটি মানের মধ্যে ডাটা ফিল্টার করতে** ব্যবহার করা হয়। এটি **inclusive**, অর্থাৎ **শুরুর মান ও শেষের মান দুটোই অন্তর্ভুক্ত করে**।  

#### **সাধারণ গঠন (Syntax)**  
```sql
SELECT column_name FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
এখানে `value1` এবং `value2` এর মধ্যে থাকা সব ডাটা **রিটার্ন** করবে।  

---

### ***প্র্যাকটিক্যাল উদাহরণ***
ধরা যাক, আমরা `Employees` টেবিল থেকে **যারা ৪০,০০০ থেকে ৫০,০০০ টাকার মধ্যে বেতন পায় তাদের খুঁজতে চাই**:  
```sql
SELECT * FROM Employees 
WHERE salary BETWEEN 40000 AND 50000;
```
এটি **৪০,০০০ থেকে ৫০,০০০ এর মধ্যে থাকা সকল salary** সহ employee দেখাবে।  

---

### **তারিখের জন্য `BETWEEN` কিভাবে কাজ করে?**
ধরুন, আমরা ২০২২ সালের মধ্যে জয়েন করা কর্মীদের দেখতে চাই:
```sql
SELECT * FROM Employees 
WHERE join_date BETWEEN '2022-01-01' AND '2022-12-31';
```
এখানে, **`join_date` যদি ১লা জানুয়ারি ২০২২ থেকে ৩১শে ডিসেম্বর ২০২২ এর মধ্যে পড়ে, তাহলে সেই সব রো রিটার্ন করবে**।  

---

### **`BETWEEN` ব্যবহার করার সুবিধা:**
✅ **কোড ছোট হয়** → `BETWEEN` ব্যবহার করলে সহজেই রেঞ্জ সেট করা যায়  
✅ **পারফরম্যান্স ভালো হয়** → এটি **ইন্ডেক্স** ব্যবহার করে কার্যকরভাবে ডাটা ফিল্টার করে  
✅ **বুঝতে সহজ** → এটি `>=` এবং `<=` এর সমতুল্য, তবে কম জটিল  

---

### **`BETWEEN` এর বিকল্প (`>=` এবং `<=`)**
উপরে দেওয়া query নিচের মত করেও লেখা যায়:
```sql
SELECT * FROM Employees 
WHERE salary >= 40000 AND salary <= 50000;
```
কিন্তু **`BETWEEN` কমপ্যাক্ট এবং সহজবোধ্য**, তাই এটিই বেশি ব্যবহৃত হয়।  


### **`IN` কিভাবে কাজ করে?**  
SQL-এ `IN` ব্যবহার করা হয় **একটি নির্দিষ্ট তালিকার মধ্যে থাকা মানগুলোর সাথে মিল আছে কিনা তা চেক করতে**। এটি `OR` কন্ডিশনের সহজতর বিকল্প।  

---

### **সাধারণ গঠন (Syntax)**  
```sql
SELECT column_name FROM table_name 
WHERE column_name IN (value1, value2, value3, ...);
```
এটি **`column_name` যদি `value1`, `value2`, বা `value3` এর কোনো একটির সমান হয়, তাহলে সেই রো রিটার্ন করবে**।  

---

### **প্র্যাকটিক্যাল উদাহরণ**  
ধরা যাক, আমরা **"HR", "IT", এবং "Finance"** ডিপার্টমেন্টের কর্মীদের খুঁজতে চাই।  

✅ **`IN` ব্যবহার করে:**  
```sql
SELECT * FROM Employees 
WHERE department IN ('HR', 'IT', 'Finance');
```
এটি **শুধুমাত্র HR, IT, এবং Finance ডিপার্টমেন্টের কর্মীদের রেকর্ড রিটার্ন করবে**।  

❌ **`OR` দিয়ে করলে:**  
```sql
SELECT * FROM Employees 
WHERE department = 'HR' OR department = 'IT' OR department = 'Finance';
```
`IN` ব্যবহার করলে কোড ছোট এবং সহজ হয়ে যায়।  

---

### **`IN` সংখ্যা বা তারিখের সাথেও কাজ করে**  
আমরা যদি **যারা ২৫, ৩০, অথবা ৩৫ বছর বয়সী তাদের খুঁজতে চাই**, তাহলে:  
```sql
SELECT * FROM Employees 
WHERE age IN (25, 30, 35);
```
এটি **২৫, ৩০ বা ৩৫ বছর বয়সী কর্মীদের রিটার্ন করবে**।  

তারিখের ক্ষেত্রেও কাজ করে:  
```sql
SELECT * FROM Employees 
WHERE join_date IN ('2022-01-10', '2023-04-18', '2021-07-01');
```
এটি শুধু **এই তিনটি তারিখে জয়েন করা কর্মীদের দেখাবে**।  

---

### **`IN` এবং `NOT IN`**
#### ✅ **`IN` → নির্দিষ্ট মানগুলোকে অন্তর্ভুক্ত করে**  
```sql
SELECT * FROM Employees 
WHERE department IN ('IT', 'Finance');
```
এটি **শুধুমাত্র IT এবং Finance ডিপার্টমেন্টের কর্মীদের দেখাবে**।  

#### ❌ **`NOT IN` → নির্দিষ্ট মানগুলো বাদ দেয়**  
```sql
SELECT * FROM Employees 
WHERE department NOT IN ('IT', 'Finance');
```
এটি **IT এবং Finance বাদ দিয়ে বাকি সব ডিপার্টমেন্টের কর্মীদের দেখাবে**।  

---

### **`IN` ব্যবহার করার সুবিধা**
✅ **কোড ছোট হয়** → `IN` ব্যবহার করলে `OR` বারবার লিখতে হয় না  
✅ **পারফরম্যান্স ভালো হতে পারে** → নির্দিষ্ট মানগুলোর জন্য **ইনডেক্স** ব্যবহার করে দ্রুত ফিল্টার করা যায়  
✅ **বোঝা সহজ** → একাধিক মান চেক করার সহজতর উপায়  



### **`LIKE` কিভাবে কাজ করে?**  
SQL-এ `LIKE` ব্যবহার করা হয় **প্যাটার্ন মিলিয়ে (pattern matching) ডাটা খুঁজতে**। এটি **`WHERE`-এর সাথে ব্যবহার করা হয়** এবং সাধারণত **`%` ও `_` wildcard** ব্যবহার করা হয়।  

---

## **✅ `LIKE` এর সাধারণ গঠন (Syntax)**
```sql
SELECT column_name FROM table_name 
WHERE column_name LIKE 'pattern';
```
এখানে **`pattern` মানের সাথে মিললে সেই রো গুলো রিটার্ন হবে।**  

---

## **🔹 `LIKE`-এ Wildcard গুলো কিভাবে কাজ করে?**  

| Wildcard | কাজ |
|----------|------------------------------------------------|
| `%` | **শূন্য বা যেকোনো সংখ্যক ক্যারেক্টার** রিপ্রেজেন্ট করে |
| `_` | **শুধুমাত্র ১টি ক্যারেক্টার** রিপ্রেজেন্ট করে |

---

## **🔸 `%` Wildcard দিয়ে উদাহরণ**
### **১️⃣ নির্দিষ্ট অক্ষর দিয়ে শুরু হওয়া ডাটা খোঁজা**
যদি আমরা এমন কর্মীদের খুঁজতে চাই **যাদের নাম 'S' দিয়ে শুরু হয়েছে**  
```sql
SELECT * FROM Employees 
WHERE name LIKE 'S%';
```
🟢 এটি **S** দিয়ে শুরু হওয়া সব নাম দেখাবে (যেমন: **Samiul, Shamima, Shakila** ইত্যাদি)।  

---

### **২️⃣ নির্দিষ্ট অক্ষর দিয়ে শেষ হওয়া ডাটা খোঁজা**
যদি আমরা এমন কর্মীদের খুঁজতে চাই **যাদের নাম 'n' দিয়ে শেষ হয়েছে**  
```sql
SELECT * FROM Employees 
WHERE name LIKE '%n';
```
🟢 এটি **n** দিয়ে শেষ হওয়া সব নাম দেখাবে (যেমন: **Jahan, Fahim, Rakibul** ইত্যাদি)।  

---

### **৩️⃣ নামের মাঝখানে নির্দিষ্ট ক্যারেক্টার থাকলে খোঁজা**
যদি আমরা এমন কর্মীদের খুঁজতে চাই **যাদের নামের মাঝে 'ah' আছে**  
```sql
SELECT * FROM Employees 
WHERE name LIKE '%ah%';
```
🟢 এটি এমন নাম দেখাবে **যেগুলোর মাঝে 'ah' আছে** (যেমন: **Shamima, Mahmud, Fahim** ইত্যাদি)।  

---

## **🔹 `_` Wildcard দিয়ে উদাহরণ**
### **১️⃣ ঠিক ১টি ক্যারেক্টার রিপ্লেস করা**
যদি আমরা এমন কর্মীদের খুঁজতে চাই **যাদের নামের দ্বিতীয় ক্যারেক্টার 'a'**  
```sql
SELECT * FROM Employees 
WHERE name LIKE '_a%';
```
🟢 এটি এমন নাম দেখাবে **যেগুলোর দ্বিতীয় ক্যারেক্টার 'a'** (যেমন: **Karim, Fahim, Samiul** ইত্যাদি)।  

---

### **২️⃣ শেষের এক ক্যারেক্টার ফিক্সড রেখে খোঁজা**
যদি আমরা এমন কর্মীদের খুঁজতে চাই **যাদের নামের শেষের আগে 'a' আছে**  
```sql
SELECT * FROM Employees 
WHERE name LIKE '%a_';
```
🟢 এটি এমন নাম দেখাবে **যেগুলোর শেষের আগে 'a' আছে** (যেমন: **Ayesha, Sumaiya** ইত্যাদি)।  

---

## **🔹 `NOT LIKE` ব্যবহার করা**
যদি আমরা এমন কর্মীদের খুঁজতে চাই **যাদের নাম 'S' দিয়ে শুরু হয়নি**  
```sql
SELECT * FROM Employees 
WHERE name NOT LIKE 'S%';
```
🟢 এটি **S দিয়ে শুরু হওয়া নাম বাদ দিয়ে বাকি সব দেখাবে**।  

---

## **✅ `LIKE` ব্যবহারের সুবিধা**
✔ **Flexible search:** নির্দিষ্ট অক্ষর দিয়ে শুরু, শেষ বা মাঝে কিছু থাকলে খুঁজতে পারে  
✔ **Wildcards:** `%` এবং `_` ব্যবহার করে কাস্টম প্যাটার্ন মিলানো যায়  
✔ **Text filtering:** নাম, ঠিকানা বা অন্য স্ট্রিং ফিল্টার করার জন্য খুবই দরকারি  

---

### **`AND`, `OR`, এবং `NOT` কিভাবে কাজ করে?**  
SQL-এ `AND`, `OR`, এবং `NOT` **লজিক্যাল অপারেটর** হিসাবে কাজ করে এবং `WHERE` ক্লজের সাথে ব্যবহার করা হয় **বিভিন্ন কন্ডিশন চেক করার জন্য**।  

---

## **✅ ১. `AND` অপারেটর (দুটি শর্ত একসাথে পূরণ করতে হবে)**
- `AND` ব্যবহার করলে **সব শর্ত একসাথে মিলে গেলে তবেই ডাটা রিটার্ন করবে**।  
- অর্থাৎ, **উভয় শর্তই সত্য হতে হবে**।  

### **উদাহরণ:**  
যদি আমরা **IT ডিপার্টমেন্টে কাজ করা এবং ৩০ বছর বা তার বেশি বয়সের কর্মীদের খুঁজতে চাই**:  
```sql
SELECT * FROM Employees 
WHERE department = 'IT' 
AND age >= 30;
```
🔹 **Result:** `department = 'IT'` এবং `age >= 30`—**উভয় শর্ত মিললে** তবেই রো রিটার্ন করবে।  

---

## **✅ ২. `OR` অপারেটর (একটি শর্ত মিললেই হবে)**
- `OR` ব্যবহার করলে **শুধুমাত্র একটি শর্ত মিললেই** ডাটা রিটার্ন করবে।  
- অর্থাৎ, **যে কোনো একটিই সত্য হতে হবে**।  

### **উদাহরণ:**  
যদি আমরা **যারা HR বা IT ডিপার্টমেন্টে কাজ করে তাদের খুঁজতে চাই**:  
```sql
SELECT * FROM Employees 
WHERE department = 'HR' 
OR department = 'IT';
```
🔹 **Result:** `HR` **অথবা** `IT` ডিপার্টমেন্টের যেকোনো কর্মী দেখাবে।  

---

## **✅ ৩. `NOT` অপারেটর (শর্ত না মিললে রিটার্ন করবে)**
- `NOT` ব্যবহার করলে **শর্তের উল্টো মান বের করে**।  
- অর্থাৎ, **যে শর্ত সত্য, সেটাকে মিথ্যা বানিয়ে ফেলে**।  

### **উদাহরণ:**  
যদি আমরা **যারা IT ডিপার্টমেন্টে নেই, তাদের দেখতে চাই**:  
```sql
SELECT * FROM Employees 
WHERE NOT department = 'IT';
```
🔹 **Result:** `IT` ডিপার্টমেন্ট বাদ দিয়ে **বাকি সব কর্মীদের দেখাবে**।  

---

## **✅ `AND`, `OR`, এবং `NOT` একসাথে ব্যবহার করা**  
আমরা চাই যে **যারা IT বা Finance ডিপার্টমেন্টে কাজ করে এবং যাদের বয়স ২৫ বছরের বেশি, তারা যেন দেখানো হয়**:  
```sql
SELECT * FROM Employees 
WHERE (department = 'IT' OR department = 'Finance') 
AND age > 25;
```
🔹 **Result:**  
- `department = 'IT'` **অথবা** `department = 'Finance'` → **যেকোনো একটি হতে হবে**  
- **এবং** `age > 25` → **বয়স ২৫-এর বেশি হতে হবে**  

---

## **✅ `NOT` সহ `AND` এবং `OR` ব্যবহার করা**  
যদি আমরা **যারা HR ডিপার্টমেন্টে নেই এবং যাদের বয়স ৩০ বছরের বেশি, শুধু তাদের দেখতে চাই**:  
```sql
SELECT * FROM Employees 
WHERE NOT department = 'HR' 
AND age > 30;
```
🔹 **Result:**  
- **HR ডিপার্টমেন্ট বাদ যাবে**  
- **যাদের বয়স ৩০ বছরের বেশি শুধু তাদের দেখাবে**  

---

## **✅ সংক্ষেপে পার্থক্য:**  

| অপারেটর | কাজ |
|----------|------------------------------------------------|
| `AND` | **সব শর্ত সত্য হতে হবে** (দুটি শর্তই মিলতে হবে) |
| `OR` | **যেকোনো এক শর্ত সত্য হলেই হবে** |
| `NOT` | **শর্তের উল্টো মান বের করে** |

---

### **`ORDER BY` কিভাবে কাজ করে?**  
SQL-এ `ORDER BY` ব্যবহার করা হয় **ডাটা সাজানোর জন্য**। এটি **বড় থেকে ছোট বা ছোট থেকে বড় ক্রমে সাজাতে পারে**।  

---

## **✅ `ORDER BY` এর সাধারণ গঠন (Syntax)**
```sql
SELECT column_name FROM table_name 
ORDER BY column_name [ASC | DESC];
```
🔹 `ASC` (Ascending) → **ছোট থেকে বড়** (default)  
🔹 `DESC` (Descending) → **বড় থেকে ছোট**  

---

## **✅ ১. `ORDER BY` দিয়ে নাম ক্রমানুসারে সাজানো**  
ধরি, আমরা **কর্মীদের নাম বর্ণানুক্রমিক (A-Z) সাজাতে চাই**:  
```sql
SELECT * FROM Employees 
ORDER BY name;
```
এটি **`name` কলামের মান A থেকে Z পর্যন্ত সাজাবে**।  

---

## **✅ ২. `ORDER BY` দিয়ে বেতন অনুযায়ী সাজানো (Ascending & Descending)**
যদি আমরা **কর্মীদের বেতন (salary) অনুযায়ী ছোট থেকে বড় (Ascending)** সাজাতে চাই:  
```sql
SELECT * FROM Employees 
ORDER BY salary ASC;
```
🟢 এটি **সবচেয়ে কম বেতন থেকে বেশি বেতনের কর্মীদের দেখাবে**।  

🔹 **বড় থেকে ছোট (Descending) সাজাতে:**  
```sql
SELECT * FROM Employees 
ORDER BY salary DESC;
```
🟢 এটি **সবচেয়ে বেশি বেতন পাওয়া কর্মীকে সবার উপরে দেখাবে**।  

---

## **✅ ৩. একাধিক কলামের উপর `ORDER BY`**  
যদি আমরা **ডিপার্টমেন্ট অনুযায়ী সাজাতে চাই এবং একই ডিপার্টমেন্টের ভেতরে বয়স অনুযায়ী (Ascending) সাজাতে চাই**:  
```sql
SELECT * FROM Employees 
ORDER BY department ASC, age ASC;
```
🔹 এটি **ডিপার্টমেন্ট অনুযায়ী সাজাবে এবং একই ডিপার্টমেন্টের মধ্যে বয়স অনুযায়ী সাজাবে**।  

---

## **✅ ৪. `ORDER BY` `WHERE` এর সাথে ব্যবহার করা**  
যদি আমরা **যারা IT ডিপার্টমেন্টে কাজ করে, শুধু তাদের বেতন অনুযায়ী সাজাতে চাই**:  
```sql
SELECT * FROM Employees 
WHERE department = 'IT' 
ORDER BY salary DESC;
```
🔹 এটি **শুধুমাত্র IT ডিপার্টমেন্টের কর্মীদের দেখাবে এবং তাদের বেতন অনুযায়ী বড় থেকে ছোট সাজাবে**।  

---

## **✅ সংক্ষেপে `ORDER BY` এর সুবিধা**
✔ **ডাটা সাজানো সহজ হয়**  
✔ **Ascending বা Descending যেকোনোভাবে সাজানো যায়**  
✔ **বড় ডাটাবেজে রিপোর্ট তৈরি করার জন্য গুরুত্বপূর্ণ**  

---

### **`NULL` এবং `NOT NULL` কিভাবে কাজ করে?**  
SQL-এ **`NULL`** মানে হলো **কোনো ডাটা নেই বা অজানা মান**, আর **`NOT NULL`** মানে হলো **ঐ কলামে অবশ্যই ডাটা থাকতে হবে**।  

---

## **✅ `NULL` ও `NOT NULL` এর সাধারণ ব্যাখ্যা**  
- **`NULL`** → যদি কোনো কলামে **মান না থাকে**, তাহলে সেটি `NULL` হবে।  
- **`NOT NULL`** → যদি কোনো কলামে `NOT NULL` দেয়া থাকে, তাহলে **সেই কলামে অবশ্যই ডাটা দিতে হবে**।  

---

## **✅ `NULL` ও `NOT NULL` টেবিল তৈরিতে কিভাবে ব্যবহার করা হয়?**  
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,  -- এখানে অবশ্যই নাম দিতে হবে
    department VARCHAR(30) NULL,  -- এখানে ডাটা না দিলেও হবে
    age INT CHECK (age >= 18),
    salary DECIMAL(10,2) NOT NULL,  -- অবশ্যই বেতন দিতে হবে
    join_date DATE NULL  -- তারিখ দেওয়া বাধ্যতামূলক না
);
```
🔹 **`NOT NULL` থাকা মানে** → ঐ কলামে ডাটা **অবশ্যই দিতে হবে**।  
🔹 **`NULL` থাকা মানে** → ঐ কলামে ডাটা **না দিলেও চলবে**।  

---

## **✅ `NULL` ডাটা ইনসার্ট করা**  
```sql
INSERT INTO employees (name, department, age, salary, join_date)  
VALUES ('Samiul', NULL, 25, 50000.00, '2022-03-15');
```
🔹 এখানে **`department` কলামে `NULL` রাখা হয়েছে**।  

---

## **✅ `NOT NULL` কলামে `NULL` দিলে কী হবে?**  
```sql
INSERT INTO employees (name, department, age, salary, join_date)  
VALUES (NULL, 'IT', 25, 50000.00, '2022-03-15');
```
⚠ **Error: Column 'name' cannot be null**  
🔹 কারণ **`name` কলামে `NOT NULL` দেয়া আছে**, তাই `NULL` দেওয়া যাবে না।  

---

## **✅ `NULL` চেক করা (WHERE সহ)**  
🔹 **`IS NULL` দিয়ে চেক করা হয় কোন কলাম `NULL` আছে কিনা**  
```sql
SELECT * FROM employees WHERE department IS NULL;
```
🔹 **যেসব কর্মীর `department` `NULL`, শুধু তাদের দেখাবে**  

🔹 **`IS NOT NULL` দিয়ে `NULL` না থাকা ডাটা খুঁজতে পারি**  
```sql
SELECT * FROM employees WHERE department IS NOT NULL;
```
🔹 **যাদের `department` এ মান আছে, শুধু তাদের দেখাবে**  

---

## **✅ `NULL` ফিল্ড আপডেট করা (`UPDATE` সহ)**  
```sql
UPDATE employees  
SET department = 'HR'  
WHERE department IS NULL;
```
🔹 **যাদের `department` `NULL`, তাদের `HR` সেট করা হবে**  

---

## **✅ `NULL` কে `DEFAULT` মান সেট করা**  
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    department VARCHAR(30) DEFAULT 'Unknown',
    age INT CHECK (age >= 18),
    salary DECIMAL(10,2) NOT NULL,
    join_date DATE NULL
);
```
🔹 **যদি `department`-এ কোনো মান না দেওয়া হয়, তাহলে স্বয়ংক্রিয়ভাবে 'Unknown' হয়ে যাবে**  

---

### 🔥 **সংক্ষেপে `NULL` এবং `NOT NULL`**  
✔ **`NULL`** → কলামে কোনো ডাটা না থাকলে `NULL` হতে পারে  
✔ **`NOT NULL`** → কলামে ডাটা থাকা বাধ্যতামূলক  
✔ **`IS NULL`** → `NULL` চেক করার জন্য  
✔ **`IS NOT NULL`** → `NULL` না থাকা চেক করার জন্য  
✔ **`UPDATE` দিয়ে `NULL` ফিল্ড আপডেট করা যায়**  

---

### **🔹 `ON` কিভাবে কাজ করে? (পূর্ণাঙ্গ উদাহরণ)**  

আমরা দুটি টেবিল তৈরি করবো:  
1. **`employees`** → কর্মীদের তথ্য থাকবে  
2. **`departments`** → ডিপার্টমেন্টের তথ্য থাকবে  

এরপর আমরা **`ON` সহ `JOIN` ব্যবহার করে** কর্মীদের সাথে তাদের ডিপার্টমেন্ট মিলিয়ে দেখাবো।  

---

### **✅ `CREATE TABLE` - টেবিল তৈরি করা**  
```sql
CREATE TABLE departments (
    id INT PRIMARY KEY,
    department_name VARCHAR(50) NOT NULL
);

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);
```
🔹 **`departments` টেবিলে প্রতিটি ডিপার্টমেন্টের নাম থাকবে।**  
🔹 **`employees` টেবিলে `department_id` ফিল্ড আছে**, যা `departments` টেবিলের `id` এর সাথে সম্পর্কিত।  

---

### **✅ `INSERT INTO` - ডাটা যোগ করা**  
```sql
INSERT INTO departments (id, department_name) VALUES
(101, 'IT'),
(102, 'HR'),
(103, 'Marketing');

INSERT INTO employees (id, name, department_id) VALUES
(1, 'Arafat', 101),
(2, 'Samiul', 102),
(3, 'Shuvo', 103),
(4, 'Alex', NULL);
```
🔹 **`departments` টেবিলে ৩টি ডিপার্টমেন্ট যোগ করা হলো।**  
🔹 **`employees` টেবিলে ৪ জন কর্মী যোগ করা হলো।**  
🔹 **Alex-এর `department_id` `NULL`, মানে সে কোনো ডিপার্টমেন্টে নেই।**  

---

### **✅ `ON` ব্যবহার করে `INNER JOIN`**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments  
ON employees.department_id = departments.id;
```
🔹 **শুধুমাত্র যাদের ডিপার্টমেন্ট আছে, তাদের দেখাবে।**  

#### **📌 Output:**  
| name   | department_name |  
|--------|---------------|  
| Arafat | IT            |  
| Samiul | HR            |  
| Shuvo  | Marketing     |  

🔹 **Alex নেই, কারণ তার `department_id` `NULL`।**  

---

### **✅ `ON` ব্যবহার করে `LEFT JOIN`**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
LEFT JOIN departments  
ON employees.department_id = departments.id;
```
🔹 **সব কর্মী দেখাবে, এমনকি যাদের ডিপার্টমেন্ট নেই তাদেরও।**  

#### **📌 Output:**  
| name   | department_name |  
|--------|---------------|  
| Arafat | IT            |  
| Samiul | HR            |  
| Shuvo  | Marketing     |  
| Alex   | NULL          |  

🔹 **Alex-এর ডিপার্টমেন্ট নেই, তাই `NULL` দেখাবে।**  

---

### **✅ `ON` এবং `USING` এর পার্থক্য**  
🔹 **যদি উভয় টেবিলে কলামের নাম আলাদা হয়, তাহলে `ON` ব্যবহার করতে হয়।**  
🔹 **যদি উভয় টেবিলে একই নামের কলাম থাকে, তাহলে `USING` ব্যবহার করা যায়।**  

#### **`ON` দিয়ে JOIN (যেহেতু কলামের নাম ভিন্ন)**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments  
ON employees.department_id = departments.id;
```

#### **`USING` দিয়ে JOIN (যদি উভয় টেবিলে `department_id` থাকে)**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments  
USING (department_id);
```

---

### 🔥 **সংক্ষেপে `ON`**  
✔ **`ON` মূলত `JOIN` এর ক্ষেত্রে ব্যবহার হয়।**  
✔ **`ON` যখন ব্যবহার করতে হয়?** → যখন দুই টেবিলের সম্পর্কিত কলামের নাম ভিন্ন হয়।  
✔ **`INNER JOIN`** → শুধুমাত্র যাদের মিল পাওয়া যায়, তাদের দেখায়।  
✔ **`LEFT JOIN`** → সব কর্মী দেখায়, এমনকি যাদের ডিপার্টমেন্ট নেই, তাদেরও।  
✔ **`USING` শুধুমাত্র ব্যবহার করা যায়, যখন কলামের নাম একই হয়।**  

---

### **🔹 `ON` কিভাবে কাজ করে? (পূর্ণাঙ্গ উদাহরণ)**  

আমরা দুটি টেবিল তৈরি করবো:  
1. **`employees`** → কর্মীদের তথ্য থাকবে  
2. **`departments`** → ডিপার্টমেন্টের তথ্য থাকবে  

এরপর আমরা **`ON` সহ `JOIN` ব্যবহার করে** কর্মীদের সাথে তাদের ডিপার্টমেন্ট মিলিয়ে দেখাবো।  

---

### **✅ `CREATE TABLE` - টেবিল তৈরি করা**  
```sql
CREATE TABLE departments (
    id INT PRIMARY KEY,
    department_name VARCHAR(50) NOT NULL
);

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);
```
🔹 **`departments` টেবিলে প্রতিটি ডিপার্টমেন্টের নাম থাকবে।**  
🔹 **`employees` টেবিলে `department_id` ফিল্ড আছে**, যা `departments` টেবিলের `id` এর সাথে সম্পর্কিত।  

---

### **✅ `INSERT INTO` - ডাটা যোগ করা**  
```sql
INSERT INTO departments (id, department_name) VALUES
(101, 'IT'),
(102, 'HR'),
(103, 'Marketing');

INSERT INTO employees (id, name, department_id) VALUES
(1, 'Arafat', 101),
(2, 'Samiul', 102),
(3, 'Shuvo', 103),
(4, 'Alex', NULL);
```
🔹 **`departments` টেবিলে ৩টি ডিপার্টমেন্ট যোগ করা হলো।**  
🔹 **`employees` টেবিলে ৪ জন কর্মী যোগ করা হলো।**  
🔹 **Alex-এর `department_id` `NULL`, মানে সে কোনো ডিপার্টমেন্টে নেই।**  

---

### **✅ `ON` ব্যবহার করে `INNER JOIN`**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments  
ON employees.department_id = departments.id;
```
🔹 **শুধুমাত্র যাদের ডিপার্টমেন্ট আছে, তাদের দেখাবে।**  

#### **📌 Output:**  
| name   | department_name |  
|--------|---------------|  
| Arafat | IT            |  
| Samiul | HR            |  
| Shuvo  | Marketing     |  

🔹 **Alex নেই, কারণ তার `department_id` `NULL`।**  

---

### **✅ `ON` ব্যবহার করে `LEFT JOIN`**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
LEFT JOIN departments  
ON employees.department_id = departments.id;
```
🔹 **সব কর্মী দেখাবে, এমনকি যাদের ডিপার্টমেন্ট নেই তাদেরও।**  

#### **📌 Output:**  
| name   | department_name |  
|--------|---------------|  
| Arafat | IT            |  
| Samiul | HR            |  
| Shuvo  | Marketing     |  
| Alex   | NULL          |  

🔹 **Alex-এর ডিপার্টমেন্ট নেই, তাই `NULL` দেখাবে।**  

---

### **✅ `ON` এবং `USING` এর পার্থক্য**  
🔹 **যদি উভয় টেবিলে কলামের নাম আলাদা হয়, তাহলে `ON` ব্যবহার করতে হয়।**  
🔹 **যদি উভয় টেবিলে একই নামের কলাম থাকে, তাহলে `USING` ব্যবহার করা যায়।**  

#### **`ON` দিয়ে JOIN (যেহেতু কলামের নাম ভিন্ন)**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments  
ON employees.department_id = departments.id;
```

#### **`USING` দিয়ে JOIN (যদি উভয় টেবিলে `department_id` থাকে)**  
```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments  
USING (department_id);
```

---

### 🔥 **সংক্ষেপে `ON`**  
✔ **`ON` মূলত `JOIN` এর ক্ষেত্রে ব্যবহার হয়।**  
✔ **`ON` যখন ব্যবহার করতে হয়?** → যখন দুই টেবিলের সম্পর্কিত কলামের নাম ভিন্ন হয়।  
✔ **`INNER JOIN`** → শুধুমাত্র যাদের মিল পাওয়া যায়, তাদের দেখায়।  
✔ **`LEFT JOIN`** → সব কর্মী দেখায়, এমনকি যাদের ডিপার্টমেন্ট নেই, তাদেরও।  
✔ **`USING` শুধুমাত্র ব্যবহার করা যায়, যখন কলামের নাম একই হয়।**  

---

### **🔹 SQL-এ `DUPLICATE TABLE` তৈরি করার উপায়**  

🔹 **কোনো টেবিলের স্ট্রাকচার ও ডাটা ক্লোন (Copy) করার জন্য `CREATE TABLE ... AS` ব্যবহার করা হয়।**  
🔹 **কোনো টেবিলের শুধুমাত্র স্ট্রাকচার ক্লোন করতে `CREATE TABLE ... LIKE` ব্যবহার করা হয়।**  

---

## **✅ ১. সম্পূর্ণ টেবিল ডুপ্লিকেট করা (`CREATE TABLE ... AS`)**  
🔹 **একটি বিদ্যমান টেবিলের সকল ডাটা সহ নতুন টেবিল তৈরি করতে:**  
```sql
CREATE TABLE employees_duplicate AS  
SELECT * FROM employees;
```
🔹 **`employees_duplicate` নামে নতুন টেবিল তৈরি হবে, যেখানে `employees` টেবিলের সব ডাটা থাকবে।**  

#### **📌 Output (নতুন `employees_duplicate` টেবিল)**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 1  | Arafat  | IT        | 50000  |  
| 2  | Samiul  | HR        | 40000  |  
| 3  | Shuvo   | Marketing | 45000  |  

---

## **✅ ২. শুধু টেবিলের স্ট্রাকচার ডুপ্লিকেট করা (`CREATE TABLE ... LIKE`)**  
🔹 **শুধু টেবিলের স্ট্রাকচার ক্লোন করতে চাইলে:**  
```sql
CREATE TABLE employees_structure LIKE employees;
```
🔹 **এতে শুধু কলামের স্ট্রাকচার কপি হবে, কিন্তু কোনো ডাটা থাকবে না।**  

#### **📌 Output (নতুন `employees_structure` টেবিল, কিন্তু খালি)**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
|    |      |           |        |  

🔹 **কোনো ডাটা নেই, কারণ `LIKE` শুধু স্ট্রাকচার কপি করে, ডাটা না।**  

---

## **✅ ৩. নির্দিষ্ট কিছু কলামের ডাটা কপি করা**  
🔹 **ধরুন, শুধু `name` এবং `salary` ডাটা সহ নতুন টেবিল তৈরি করতে চাই:**  
```sql
CREATE TABLE high_salary_employees AS  
SELECT name, salary FROM employees WHERE salary > 40000;
```
🔹 **শুধুমাত্র যাদের `salary > 40000` তারা `high_salary_employees` টেবিলে থাকবে।**  

#### **📌 Output (নতুন `high_salary_employees` টেবিল)**  
| name   | salary  |  
|--------|--------|  
| Arafat | 50000  |  
| Shuvo  | 45000  |  

---

## **✅ ৪. টেবিল ডুপ্লিকেট করার পরে নতুন ডাটা যোগ করা**  
```sql
INSERT INTO employees_duplicate (id, name, department, salary)  
VALUES (4, 'Alex', 'Finance', 42000);
```
🔹 **এতে `employees_duplicate` টেবিলে নতুন রো যোগ হবে, কিন্তু `employees` টেবিল অক্ষত থাকবে।**  

---

## 🔥 **সংক্ষেপে `DUPLICATE TABLE`**  
✔ **`CREATE TABLE new_table AS SELECT * FROM old_table;`** → টেবিলের স্ট্রাকচার ও ডাটা কপি করবে।  
✔ **`CREATE TABLE new_table LIKE old_table;`** → শুধুমাত্র স্ট্রাকচার কপি করবে, কোনো ডাটা থাকবে না।  
✔ **নির্দিষ্ট কলামের ডাটা কপি করতে `SELECT column1, column2 FROM table` ব্যবহার করা যায়।**  

---
### **🔹 `dummy_employee` নামে `employees` টেবিলের ডুপ্লিকেট তৈরি করা**  

🔹 **আপনি `employees` টেবিলের সব ডাটা ও স্ট্রাকচার কপি করতে পারেন নিচের দুটি পদ্ধতিতে:**  

---

### **✅ `CREATE TABLE ... AS SELECT * FROM` (ডাটা ও স্ট্রাকচার কপি করবে)**  
```sql
CREATE TABLE dummy_employee AS  
SELECT * FROM employees;
```
🔹 **এটি `employees` টেবিলের সব কলাম ও ডাটা `dummy_employee` টেবিলে কপি করবে।**  

---

### **✅ `CREATE TABLE ... LIKE` (শুধুমাত্র স্ট্রাকচার কপি করবে, ডাটা থাকবে না)**  
```sql
CREATE TABLE dummy_employee LIKE employees;
```
🔹 **এতে `dummy_employee` টেবিল `employees` এর মতোই হবে, কিন্তু কোনো ডাটা থাকবে না।**  
🔹 **ডাটা যোগ করতে চাইলে:**  
```sql
INSERT INTO dummy_employee SELECT * FROM employees;
```

---

### **✅ নিশ্চিত করার জন্য `SELECT` করে দেখুন:**  
```sql
SELECT * FROM dummy_employee;
```
🔹 **এতে `dummy_employee` টেবিলের সব ডাটা দেখতে পাবেন।**  

---
### **🔹 `dummy_employee` টেবিল ব্যবহার করে `LIMIT` বুঝিয়ে দেওয়া**  

এখন থেকে **`dummy_employee`** টেবিল নিয়ে কাজ করবো এবং `LIMIT` সম্পর্কে বিস্তারিত দেখাবো।  

---

## **✅ `LIMIT` দিয়ে নির্দিষ্ট সংখ্যক রো দেখানো**  
🔹 প্রথম **৫ জন কর্মী** দেখাতে চাইলে:  
```sql
SELECT * FROM dummy_employee  
LIMIT 5;
```
🔹 **📌 Output:**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 1  | Arafat  | IT        | 50000  |  
| 2  | Samiul  | HR        | 40000  |  
| 3  | Shuvo   | Marketing | 45000  |  
| 4  | Alex    | Finance   | 42000  |  
| 5  | John    | IT        | 46000  |  

---

## **✅ `LIMIT` + `ORDER BY` (সবচেয়ে বেশি বেতনের ৩ জন কর্মী দেখানো)**  
```sql
SELECT * FROM dummy_employee  
ORDER BY salary DESC  
LIMIT 3;
```
🔹 **📌 Output:**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 1  | Arafat  | IT        | 50000  |  
| 5  | John    | IT        | 46000  |  
| 3  | Shuvo   | Marketing | 45000  |  

---

## **✅ `LIMIT` + `OFFSET` (দ্বিতীয় পৃষ্ঠার ডাটা আনতে)**  
🔹 প্রথম **৫টি রো বাদ দিয়ে পরের ৫টি রো দেখতে চাইলে:**  
```sql
SELECT * FROM dummy_employee  
LIMIT 5 OFFSET 5;
```
🔹 **📌 Output:**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 6  | Michael | HR        | 39000  |  
| 7  | Sarah   | IT        | 42000  |  
| 8  | David   | Finance   | 41000  |  
| 9  | Emma    | HR        | 43000  |  
| 10 | James   | IT        | 40000  |  

---

## **✅ `LIMIT` + `WHERE` (শর্ত দিয়ে নির্দিষ্ট সংখ্যক রো দেখানো)**  
🔹 **শুধুমাত্র `IT` ডিপার্টমেন্টের প্রথম ২ জন কর্মী দেখতে চাইলে:**  
```sql
SELECT * FROM dummy_employee  
WHERE department = 'IT'  
LIMIT 2;
```
🔹 **📌 Output:**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 1  | Arafat  | IT        | 50000  |  
| 5  | John    | IT        | 46000  |  

---

## **✅ `LIMIT` + `DELETE` (শুধু নির্দিষ্ট সংখ্যক রো মুছতে)**  
🔹 যদি **শুধু প্রথম ৩ জন কর্মী ডিলিট করতে চাই:**  
```sql
DELETE FROM dummy_employee  
ORDER BY id ASC  
LIMIT 3;
```
🔹 **📌 Result:** প্রথম ৩ জন কর্মী **মুছে যাবে।**  

---

## **🔥 সংক্ষেপে `LIMIT`**  
✔ **`LIMIT n`** → প্রথম `n` সংখ্যক রো দেখায়।  
✔ **`LIMIT n OFFSET m`** → প্রথম `m` রো বাদ দিয়ে পরের `n` রো দেখায়।  
✔ **`ORDER BY` + `LIMIT`** → বড় বা ছোট মানের শীর্ষ `n` টা রো দেখাতে সাহায্য করে।  
✔ **`WHERE` + `LIMIT`** → শর্ত অনুযায়ী নির্দিষ্ট সংখ্যক রো ফিল্টার করে।  
✔ **`DELETE` + `LIMIT`** → নির্দিষ্ট সংখ্যক রো ডিলিট করে।  

---


### **🔹 SQL-এ `OFFSET` কীভাবে কাজ করে?**  
🔹 **`OFFSET` সাধারণত `LIMIT` এর সাথে ব্যবহার হয়, যা নির্দিষ্ট সংখ্যক রো স্কিপ (বাদ) করে পরের ডাটা দেখাতে সাহায্য করে।**  
🔹 এটি **পেজিনেশন (pagination)** করার জন্য অনেক বেশি ব্যবহৃত হয়।  

---

## **✅ `LIMIT` vs `LIMIT + OFFSET`**  
📌 **কেবল `LIMIT` দিলে:** প্রথম `n` সংখ্যক রো দেখাবে।  
📌 **`LIMIT + OFFSET` দিলে:** প্রথম `OFFSET` সংখ্যক রো বাদ দিয়ে, পরের `LIMIT` সংখ্যক রো দেখাবে।  

---

## **✅ `OFFSET` সহ `dummy_employee` টেবিলে কাজ করা**  

### **১️⃣ প্রথম ৫ জন কর্মী দেখানো (`LIMIT` ব্যবহার করে)**  
```sql
SELECT * FROM dummy_employee  
LIMIT 5;
```
🔹 **Result:**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 1  | Arafat  | IT        | 50000  |  
| 2  | Samiul  | HR        | 40000  |  
| 3  | Shuvo   | Marketing | 45000  |  
| 4  | Alex    | Finance   | 42000  |  
| 5  | John    | IT        | 46000  |  

---

### **২️⃣ প্রথম ৫টি রো বাদ দিয়ে, পরের ৫টি রো দেখানো (`OFFSET` ব্যবহার করে)**  
```sql
SELECT * FROM dummy_employee  
LIMIT 5 OFFSET 5;
```
🔹 **Result:**  
| id | name    | department | salary  |  
|----|--------|-----------|--------|  
| 6  | Michael | HR        | 39000  |  
| 7  | Sarah   | IT        | 42000  |  
| 8  | David   | Finance   | 41000  |  
| 9  | Emma    | HR        | 43000  |  
| 10 | James   | IT        | 40000  |  

📌 **এখানে প্রথম ৫টি রো বাদ দেওয়া হয়েছে, তাই রেজাল্ট শুরু হয়েছে `id = 6` থেকে।**  

---

### **৩️⃣ ১০টি রো বাদ দিয়ে, পরের ৫টি রো দেখানো**  
```sql
SELECT * FROM dummy_employee  
LIMIT 5 OFFSET 10;
```
🔹 **Result:**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 11 | Robert  | Finance   | 45000  |  
| 12 | Sophia  | HR        | 39000  |  
| 13 | William | IT        | 47000  |  
| 14 | Olivia  | Marketing | 41000  |  
| 15 | Daniel  | IT        | 43000  |  

📌 **এবার প্রথম ১০টি রো বাদ দেওয়া হয়েছে, তাই রেজাল্ট শুরু হয়েছে `id = 11` থেকে।**  

---

## **✅ `ORDER BY` + `OFFSET` (বেশি বেতনের কর্মীদের মধ্যে ৫-১০ নম্বর অবস্থানে থাকা কর্মীরা)**  
```sql
SELECT * FROM dummy_employee  
ORDER BY salary DESC  
LIMIT 5 OFFSET 5;
```
🔹 **Result:**  
| id | name  | department | salary  |  
|----|------|-----------|--------|  
| 6  | Michael | HR        | 39000  |  
| 7  | Sarah   | IT        | 42000  |  
| 8  | David   | Finance   | 41000  |  
| 9  | Emma    | HR        | 43000  |  
| 10 | James   | IT        | 40000  |  

📌 **এখানে বেশি বেতনের **শীর্ষ ৫ জন বাদ দিয়ে, পরের ৫ জনকে দেখানো হয়েছে।**  

---

## **✅ `DELETE` + `OFFSET` (প্রথম ৫ জন বাদ দিয়ে, পরের ৩ জন কর্মী ডিলিট করা)**  
```sql
DELETE FROM dummy_employee  
ORDER BY id ASC  
LIMIT 3 OFFSET 5;
```
📌 **এতে প্রথম ৫ জন বাদ দিয়ে, পরের ৩ জন কর্মী ডিলিট হবে।**  

---

## **🔥 সংক্ষেপে `OFFSET`**  
✔ **`LIMIT n`** → প্রথম `n` সংখ্যক রো দেখাবে।  
✔ **`LIMIT n OFFSET m`** → প্রথম `m` সংখ্যক রো বাদ দিয়ে, পরের `n` সংখ্যক রো দেখাবে।  
✔ **`ORDER BY` + `OFFSET`** → কোনো নির্দিষ্ট ক্রমে (সর্বোচ্চ বা সর্বনিম্ন) কিছু রো বাদ দিয়ে দেখানো যায়।  
✔ **`DELETE` + `OFFSET`** → নির্দিষ্ট সংখ্যক রো বাদ দিয়ে কিছু রো মুছে ফেলা যায়।  

---

### **🔹 `GROUP BY` কীভাবে কাজ করে?**

**`GROUP BY`** SQL-এর একটি শক্তিশালী ক্লজ যা ব্যবহার করে ডাটাকে এক বা একাধিক কলামের ভিত্তিতে **গ্রুপ** করা হয় এবং সাধারণত **অ্যাগ্রিগেট ফাংশন** (যেমন `SUM`, `AVG`, `COUNT`, `MIN`, `MAX`) এর সাথে ব্যবহৃত হয়। এটি আপনাকে ডাটা গ্রুপ করে প্রতিটি গ্রুপের উপর ফাংশন প্রয়োগ করতে সাহায্য করে।  

---

### **✅ `GROUP BY` এর সেগমেন্ট:**

1. **`GROUP BY` একটি বা একাধিক কলাম নিয়ে গ্রুপ করে।**
2. **অ্যাগ্রিগেট ফাংশন** শুধুমাত্র গ্রুপের উপর কাজ করে।
3. **`HAVING`** (যা `WHERE` এর মতো) গ্রুপের উপর শর্ত দেয়, কিন্তু `WHERE` শুধুমাত্র রেকর্ডগুলোর উপর কাজ করে।

---

### **✅ উদাহরণ ১: `GROUP BY` এক কলাম দিয়ে**

ধরা যাক **`dummy_employee`** টেবিলে কর্মীদের বেতন দেখানোর পাশাপাশি, **ডিপার্টমেন্ট অনুযায়ী গড় বেতন** দেখতে চাই।

#### **`GROUP BY` দিয়ে `department` অনুযায়ী গড় বেতন বের করা:**
```sql
SELECT department, AVG(salary) AS avg_salary 
FROM dummy_employee
GROUP BY department;
```

🔹 **Result:**  
| department | avg_salary |  
|------------|------------|  
| IT         | 47000.00   |  
| HR         | 42000.00   |  
| Marketing  | 43000.00   |  
| Finance    | 42000.00   |  

---

### **✅ উদাহরণ ২: `GROUP BY` একাধিক কলাম দিয়ে**

ধরা যাক, আপনি ডিপার্টমেন্ট এবং বেতন অনুসারে কর্মীদের **গণনা** করতে চান। আপনি দুটি কলাম ব্যবহার করতে পারেন — `department` এবং `salary`।

#### **`GROUP BY` দিয়ে `department` এবং `salary` অনুযায়ী মোট কর্মী গণনা:**
```sql
SELECT department, salary, COUNT(*) AS total_employees
FROM dummy_employee
GROUP BY department, salary;
```

🔹 **Result:**  
| department | salary | total_employees |  
|------------|--------|-----------------|  
| IT         | 50000  | 2               |  
| HR         | 39000  | 1               |  
| Marketing  | 45000  | 1               |  
| Finance    | 42000  | 1               |  
| IT         | 46000  | 1               |  
| HR         | 43000  | 1               |  
| Marketing  | 41000  | 1               |  

---

### **✅ `GROUP BY` + `HAVING`**

**`HAVING`** হল একটি শর্ত যা **`GROUP BY`** এর পরে ব্যবহৃত হয়, এবং এটি গ্রুপ করা রেকর্ডের উপর শর্ত প্রয়োগ করে। এটি **`WHERE`** এর মতো কাজ করে, তবে **`WHERE`** কেবল রেকর্ডের জন্য ব্যবহার করা যায়, আর **`HAVING`** গ্রুপের জন্য।

#### **উদাহরণ:**  
যদি আপনি চাচ্ছেন, এমন ডিপার্টমেন্টগুলো দেখাতে যেখানে গড় বেতন ৪৫০০০ টাকার বেশি:

```sql
SELECT department, AVG(salary) AS avg_salary 
FROM dummy_employee
GROUP BY department
HAVING AVG(salary) > 45000;
```

🔹 **Result:**  
| department | avg_salary |  
|------------|------------|  
| IT         | 47000.00   |  

---

### **✅ `GROUP BY` + `ORDER BY`**

আপনি **`GROUP BY`** এর সাথে **`ORDER BY`** ব্যবহার করে গ্রুপের রেজাল্টগুলো নির্দিষ্ট অর্ডারে সাজাতে পারেন।

#### **উদাহরণ:**  
**`department` অনুযায়ী গড় বেতন দেখানোর পাশাপাশি, `avg_salary` অনুসারে সাজানো:**

```sql
SELECT department, AVG(salary) AS avg_salary 
FROM dummy_employee
GROUP BY department
ORDER BY avg_salary DESC;
```

🔹 **Result:**  
| department | avg_salary |  
|------------|------------|  
| IT         | 47000.00   |  
| Marketing  | 43000.00   |  
| Finance    | 42000.00   |  
| HR         | 42000.00   |  

---

### **🔥 সংক্ষেপে `GROUP BY`:**

- **`GROUP BY column`** → একটি কলাম (বা একাধিক কলাম) ব্যবহার করে রেকর্ডগুলো গ্রুপ করে।
- **`HAVING`** → `GROUP BY` এর পরে শর্ত দেয় (গ্রুপের ওপর)।
- **`ORDER BY`** → গ্রুপগুলিকে সাজাতে ব্যবহৃত হয়।
- **অ্যাগ্রিগেট ফাংশন** (যেমন `AVG`, `SUM`, `COUNT`, `MIN`, `MAX`) গ্রুপের উপর কাজ করে।

---

### **🔹 SQL-এ `MIN`, `MAX`, `COUNT`, `AVG`, `SUM` ফাংশন**  
এই ফাংশনগুলো SQL এ **অ্যাগ্রিগেট ফাংশন** (Aggregate Functions) হিসেবে পরিচিত, যেগুলি ডাটার উপর গণনা করার জন্য ব্যবহৃত হয়। এগুলো সাধারণত **`GROUP BY`** এবং **`WHERE`** এর সাথে ব্যবহার করা হয়, কিন্তু এককভাবে ডাটার মোটামুটি এক্সট্র্যাক্ট করতে পারা যায়।  

---

### **✅ ১. `MIN` (সর্বনিম্ন মান)**  
🔹 **`MIN` ফাংশন একটি কলামে সর্বনিম্ন মান খুঁজে বের করে।**

#### **উদাহরণ:**  
**`dummy_employee` টেবিলের `salary` কলাম থেকে সর্বনিম্ন বেতন খুঁজে বের করা:**
```sql
SELECT MIN(salary) AS min_salary FROM dummy_employee;
```
🔹 **Result:**  
| min_salary |  
|------------|  
| 39000      |  

---

### **✅ ২. `MAX` (সর্বোচ্চ মান)**  
🔹 **`MAX` ফাংশন একটি কলামে সর্বোচ্চ মান খুঁজে বের করে।**

#### **উদাহরণ:**  
**`dummy_employee` টেবিলের `salary` কলাম থেকে সর্বোচ্চ বেতন খুঁজে বের করা:**
```sql
SELECT MAX(salary) AS max_salary FROM dummy_employee;
```
🔹 **Result:**  
| max_salary |  
|------------|  
| 50000      |  

---

### **✅ ৩. `COUNT` (ডাটা সংখ্যা গোনা)**  
🔹 **`COUNT` ফাংশন কোনো কলামে মোট রেকর্ডের সংখ্যা গণনা করে।**

#### **উদাহরণ:**  
**`dummy_employee` টেবিলের মোট কর্মীর সংখ্যা জানার জন্য:**
```sql
SELECT COUNT(*) AS total_employees FROM dummy_employee;
```
🔹 **Result:**  
| total_employees |  
|-----------------|  
| 15              |  

---

### **✅ ৪. `AVG` (গড় মান)**  
🔹 **`AVG` ফাংশন কোনো কলামের গড় মান বের করে।**

#### **উদাহরণ:**  
**`dummy_employee` টেবিলের `salary` কলামের গড় বেতন বের করা:**
```sql
SELECT AVG(salary) AS avg_salary FROM dummy_employee;
```
🔹 **Result:**  
| avg_salary |  
|------------|  
| 43500.00   |  

---

### **✅ ৫. `SUM` (মোট মান)**  
🔹 **`SUM` ফাংশন কোনো কলামে সব মানের যোগফল বের করে।**

#### **উদাহরণ:**  
**`dummy_employee` টেবিলের `salary` কলামের মোট বেতন বের করা:**
```sql
SELECT SUM(salary) AS total_salary FROM dummy_employee;
```
🔹 **Result:**  
| total_salary |  
|--------------|  
| 652500      |  

---

### **📌 একত্রে ব্যবহার**  
**যদি সব ফাংশন একসাথে ব্যবহার করতে চান:**  
```sql
SELECT 
    MIN(salary) AS min_salary,
    MAX(salary) AS max_salary,
    COUNT(*) AS total_employees,
    AVG(salary) AS avg_salary,
    SUM(salary) AS total_salary
FROM dummy_employee;
```

🔹 **Result:**  
| min_salary | max_salary | total_employees | avg_salary | total_salary |  
|------------|------------|-----------------|------------|--------------|  
| 39000      | 50000      | 15              | 43500.00   | 652500       |  

---

### **🔥 সংক্ষেপে ফাংশনগুলো:**

- **`MIN(column)`** → কলামের সর্বনিম্ন মান।
- **`MAX(column)`** → কলামের সর্বোচ্চ মান।
- **`COUNT(*)`** → মোট রেকর্ড সংখ্যা।
- **`AVG(column)`** → কলামের গড় মান।
- **`SUM(column)`** → কলামের সব মানের যোগফল।

---
