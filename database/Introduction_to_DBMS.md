<h1>Data, Information & Database</h1>
<h2>1. What is Data?</h2>
<p>
  Data refers to raw, unprocessed facts and figures. It can exist in forms such
  as numbers, text, symbols, images, or sounds, and does not carry specific
  meaning by itself. When organized or processed, data becomes meaningful
  information.
</p>

<img
  src="/1-tHtE29Sw.png"
  alt=""
  style="display: block; margin: 0 auto"
/>

<h3>Types of Data</h3>
<table>
  <tr>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>Numerical</td>
    <td>Data represented by numbers</td>
    <td>123, 45.67, -34</td>
  </tr>
  <tr>
    <td>Textual</td>
    <td>Data represented in words or characters</td>
    <td>"Hello", "Database"</td>
  </tr>
  <tr>
    <td>Boolean</td>
    <td>Data represented in true or false values</td>
    <td>true, false</td>
  </tr>
  <tr>
    <td>Categorical</td>
    <td>Data categorized into distinct groups or classes</td>
    <td>Male/Female, Product A/B/C</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h2>2. Data Hierarchy</h2>
<p>
  Data hierarchy represents the levels of data organization, starting with the
  smallest element and moving to complex levels for meaningful information.
</p>

<table>
  <tr>
    <th>Level</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>Bit</td>
    <td>The smallest unit of data, represented as 0 or 1</td>
    <td>0, 1</td>
  </tr>
  <tr>
    <td>Byte</td>
    <td>8 bits make up a byte</td>
    <td>ASCII code for "A" is 65</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h2>3. What is Information?</h2>
<p>
  Information is data that has been processed and organized in a way that adds
  meaning, making it useful for decision-making.
</p>

<h3>Example: Data vs. Information</h3>
<table>
  <tr>
    <th>Data</th>
    <th>Information</th>
  </tr>
  <tr>
    <td>{Marks: [55, 78, 62, 85]}</td>
    <td>"Average Marks: 70"</td>
  </tr>
</table>
<!-- <hr class="line-break" /> -->
<h2>4. What is a Database?</h2>
<p>
  A database is a structured collection of data that can be accessed, managed,
  and updated efficiently. Databases are essential for storing information in an
  organized way.
</p>

<h3>Types of Databases</h3>
<table>
  <tr>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>Relational Database</td>
    <td>Uses tables (relations) to organize data</td>
    <td>MySQL, PostgreSQL</td>
  </tr>
</table>

<h3>Code Example: SQL Query in a Relational Database</h3>
<pre>
            SELECT first_name, last_name, age 
            FROM students 
            WHERE age > 18;
        </pre
>

<!-- <hr class="line-break" /> -->
<h2>5. Characteristics of a Database</h2>
<table>
  <tr>
    <th>Characteristic</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Data Integrity</td>
    <td>Ensures data accuracy and consistency</td>
  </tr>
</table>

<p>In summary:</p>
<ul>
  <li><strong>Data</strong> is raw, unprocessed facts.</li>
  <li><strong>Information</strong> is meaningful and organized data.</li>
  <li>
    A <strong>database</strong> efficiently stores, manages, and retrieves data,
    with key characteristics like data integrity, security, and scalability.
  </li>
</ul>
<br />
<hr class="line-break" />
<h1>Types of Databases</h1>

<img
  src="/time-by1SMUm-.png"
  alt=""
  style="display: block; margin: 0 auto"
/>

<h2>1. Relational Databases</h2>
<p>
  Definition: Relational databases store data in tables with rows and columns,
  using structured query language (SQL) for querying. They rely on a schema to
  define data organization and enforce data integrity through rules and
  constraints. In a relational database, data is structured, and relationships
  between tables are established using primary and foreign keys.
</p>
<h3>Characteristics:</h3>
<ul>
  <li>Structured data: Organized into tables, making it easy to understand.</li>
  <li>
    ACID compliance: Ensures data integrity with Atomicity, Consistency,
    Isolation, and Durability.
  </li>
  <li>Relationships: Data can be linked through primary and foreign keys.</li>
  <li>
    Scalability: Typically scales vertically (adding more resources to a single
    server).
  </li>
</ul>

<h3>Example: University Student Records</h3>
<p>
  Imagine a university database with three tables: Students, Courses, and
  Enrollments.
</p>
<h4>Table Structure:</h4>
<table>
  <tr>
    <th>Table</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Students</td>
    <td>
      Stores student information with columns student_id, name, age, major.
    </td>
  </tr>
  <tr>
    <td>Courses</td>
    <td>
      Stores course information with columns course_id, course_name, credits.
    </td>
  </tr>
  <tr>
    <td>Enrollments</td>
    <td>
      Links students to courses, using student_id and course_id as foreign keys.
    </td>
  </tr>
</table>

<h3>Practical Example</h3>
<pre>
<code>CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    major VARCHAR(50)
);
CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(50),
    credits INT
);
CREATE TABLE Enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);
</code>
</pre>

<h3>Example Query: Find students enrolled in "Database Systems."</h3>
<pre>
<code>SELECT Students.name, Courses.course_name
FROM Students
JOIN Enrollments ON Students.student_id = Enrollments.student_id
JOIN Courses ON Enrollments.course_id = Courses.course_id
WHERE Courses.course_name = 'Database Systems';
</code>
</pre>

<h3>Schema Definitions for the Tables</h3>
<h4>Table: Students</h4>
<table>
  <tr>
    <th>Column</th>
    <th>Data Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>student_id</td>
    <td>INT (Primary Key)</td>
    <td>Unique ID for each student</td>
  </tr>
  <tr>
    <td>name</td>
    <td>VARCHAR(50)</td>
    <td>Name of the student</td>
  </tr>
  <tr>
    <td>age</td>
    <td>INT</td>
    <td>Age of the student</td>
  </tr>
  <tr>
    <td>major</td>
    <td>VARCHAR(50)</td>
    <td>Student's major/field</td>
  </tr>
</table>

<h4>Table: Courses</h4>
<table>
  <tr>
    <th>Column</th>
    <th>Data Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>course_id</td>
    <td>INT (Primary Key)</td>
    <td>Unique ID for each course</td>
  </tr>
  <tr>
    <td>course_name</td>
    <td>VARCHAR(50)</td>
    <td>Name of the course</td>
  </tr>
  <tr>
    <td>credits</td>
    <td>INT</td>
    <td>Credit hours for the course</td>
  </tr>
</table>

<h4>Table: Enrollments</h4>
<table>
  <tr>
    <th>Column</th>
    <th>Data Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>enrollment_id</td>
    <td>INT (Primary Key)</td>
    <td>Unique ID for each enrollment record</td>
  </tr>
  <tr>
    <td>student_id</td>
    <td>INT (Foreign Key)</td>
    <td>References student_id in Students table</td>
  </tr>
  <tr>
    <td>course_id</td>
    <td>INT (Foreign Key)</td>
    <td>References course_id in Courses table</td>
  </tr>
</table>

<h3>Use Cases</h3>
<p>
  Banking systems, inventory management, and academic records where structured
  data and relationships are essential.
</p>

<!-- <hr class="line-break" /> -->
<h2>2. NoSQL Databases</h2>
<p>
  Definition: NoSQL databases are non-relational and ideal for storing large
  volumes of unstructured or semi-structured data. They offer flexibility in
  schema, allowing changes without affecting the entire database structure.
  NoSQL stands for "Not Only SQL," which means these databases can support other
  querying mechanisms beyond SQL.
</p>
<h3>Characteristics:</h3>
<ul>
  <li>Flexible schema: Adaptable to evolving data structures.</li>
  <li>
    High scalability: Often horizontally scalable, handling large amounts of
    data.
  </li>
  <li>
    Variety: Includes document, key-value, column-family, and graph databases.
  </li>
  <li>
    Distributed: Many NoSQL databases are designed for distributed environments.
  </li>
</ul>

<h3>Example: E-commerce Product Inventory (Document-Oriented)</h3>
<pre>
<code>{
    "_id": 1,
    "name": "Laptop",
    "category": "Electronics",
    "price": 899.99,
    "stock": 50,
    "details": {
        "brand": "BrandX",
        "features": ["8GB RAM", "256GB SSD", "Intel i5"]
    }
}
</code>
</pre>

<h3>MongoDB Query Example</h3>
<pre>
<code>db.Products.find({ price: { $gt: 500 } });
</code>
</pre>

<img
  src="/types-Ph9B2SNA.png"
  alt=""
  style="display: block; margin: 0 auto"
/>
<br />

<!-- <hr class="line-break" /> -->
<h2>3. Hierarchical Databases</h2>
<p>
  Definition: Hierarchical databases organize data in a tree-like structure,
  where each record has a single parent and possibly multiple children. This
  model is based on a parent-child relationship, making it suitable for
  representing one-to-many relationships.
</p>
<h3>Characteristics:</h3>
<ul>
  <li>
    Rigid structure: Based on predefined relationships; does not allow
    many-to-many relationships.
  </li>
  <li>
    High performance: Good for applications where data relationships are
    hierarchical and unlikely to change.
  </li>
  <li>Fast data retrieval: Efficient for navigational access.</li>
</ul>

<h3>Example: Company Organizational Structure</h3>
<table>
  <tr>
    <th>Level</th>
    <th>Employee Name</th>
    <th>Reports To</th>
  </tr>
  <tr>
    <td>CEO</td>
    <td>John Smith</td>
    <td>NULL</td>
  </tr>
  <tr>
    <td>VP of Marketing</td>
    <td>Sarah Johnson</td>
    <td>John Smith</td>
  </tr>
  <tr>
    <td>Marketing Manager 1</td>
    <td>Emily Brown</td>
    <td>Sarah Johnson</td>
  </tr>
  <tr>
    <td>VP of Sales</td>
    <td>Michael Green</td>
    <td>John Smith</td>
  </tr>
</table>

<h3>Use Cases</h3>
<p>Telecommunications directories, organizational charts, and file systems.</p>

<!-- <hr class="line-break" /> -->
<h2>4. Network Databases</h2>
<p>
  Definition: Network databases use a graph structure to handle complex
  relationships with many-to-many connections. Data is organized as records
  connected by links, making it useful for applications with highly
  interconnected data.
</p>
<h3>Characteristics:</h3>
<ul>
  <li>Flexible relationships: Supports complex many-to-many relationships.</li>
  <li>
    Performance: Efficient for applications with complex data relationships.
  </li>
  <li>
    Navigational: Data access paths are pre-defined, enhancing query
    performance.
  </li>
</ul>

<h3>Example: Social Network Connections</h3>
<table>
  <tr>
    <th>User ID</th>
    <th>Name</th>
    <th>Connected To (User ID)</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Alice</td>
    <td>2, 3</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Bob</td>
    <td>1, 3, 4</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Charlie</td>
    <td>1, 2</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Dave</td>
    <td>2</td>
  </tr>
</table>

<h3>Use Cases</h3>
<p>Social networks, telecommunication networks, and supply chain management.</p>

<!-- <hr class="line-break" /> -->
<h2>5. Object-Oriented Databases</h2>
<p>
  Definition: Object-oriented databases store data as objects, similar to the
  objects used in object-oriented programming (OOP). These databases integrate
  with OOP languages, allowing complex data types and supporting inheritance,
  polymorphism, and encapsulation.
</p>
<h3>Characteristics:</h3>
<ul>
  <li>
    Data as objects: Stores data in object form, supporting OOP principles.
  </li>
  <li>
    Complex data types: Allows for nested objects and complex relationships.
  </li>
  <li>
    Direct mapping: Simplifies application-database integration for OOP
    languages.
  </li>
</ul>

<h3>Example: Library System</h3>
<pre>
<code>class Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn

    def display_info(self):
        return f"{self.title} by {self.author}, ISBN: {self.isbn}"

</code>
</pre>

<p>Each Book object represents a record in the database.</p>

<h3>Use Cases</h3>
<p>
  CAD/CAM systems, multimedia applications, and applications where data
  structure is complex and hierarchical.
</p>

<hr class="line-break" />
<h1>Database Management System</h1>

<h2>1. What is a DBMS?</h2>
<p>
  A Database Management System (DBMS) is software designed to define, create,
  manage, and control access to a database. It provides an interface between the
  end-users or applications and the database, making it easy to perform
  operations like data storage, retrieval, and modification. Examples of DBMS
  include MySQL, PostgreSQL, Oracle Database, and Microsoft SQL Server.
</p>

<h3>Key Functions of DBMS</h3>
<ul>
  <li>
    Data Definition: Allows defining the structure of data within the database.
  </li>
  <li>Data Manipulation: Enables data to be inserted, updated, or deleted.</li>
  <li>Data Security: Provides access control mechanisms to secure data.</li>
  <li>Data Integrity: Ensures data accuracy and consistency.</li>
  <li>
    Data Recovery: Offers backup and recovery functions in case of data loss.
  </li>
</ul>
<br />
<!-- <hr class="line-break" /> -->
<h2>2. Database vs. File System</h2>
<p>
  File systems are a simpler way to store data in files or folders on a
  computer. While file systems allow data storage, they lack complex
  functionalities like data integrity checks, data retrieval, and transaction
  management. The DBMS offers these advanced features, providing a more
  efficient way of organizing and managing large datasets.
</p>

<table>
  <tr>
    <th>Feature</th>
    <th>File System</th>
    <th>DBMS</th>
  </tr>
  <tr>
    <td>Data Redundancy</td>
    <td>High (data duplication)</td>
    <td>Low (redundancy minimized)</td>
  </tr>
  <tr>
    <td>Data Access</td>
    <td>Sequential and less efficient</td>
    <td>Faster, optimized with indexes</td>
  </tr>
  <tr>
    <td>Data Integrity</td>
    <td>Limited checks</td>
    <td>Enforced by constraints</td>
  </tr>
  <tr>
    <td>Security</td>
    <td>Basic file permissions</td>
    <td>Granular access control</td>
  </tr>
  <tr>
    <td>Concurrency</td>
    <td>No or limited support</td>
    <td>Handles concurrent users</td>
  </tr>
  <tr>
    <td>Backup/Recovery</td>
    <td>Manual backup</td>
    <td>Automated, with recovery tools</td>
  </tr>
  <tr>
    <td>Transaction</td>
    <td>None</td>
    <td>ACID properties for reliability</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h2>3. Why is DBMS Important?</h2>
<p>
  DBMS has become essential in managing data for various industries due to its
  advantages over traditional file-based systems. Here’s why it matters:
</p>
<ul>
  <li>Data Integrity and Accuracy: Ensures data is accurate and consistent.</li>
  <li>
    Efficient Data Management: Organizes large datasets, making data
    manipulation faster.
  </li>
  <li>
    Enhanced Security: Provides multi-layer security to prevent unauthorized
    access.
  </li>
  <li>
    Data Recovery: Ensures data safety with backup and recovery functions.
  </li>
  <li>
    Scalability: Easily scales to handle growing data volumes, making it
    suitable for enterprise use.
  </li>
</ul>

<h3>Practical Use Case: E-commerce Inventory Management</h3>
<p>
  Consider an online store managing product inventory. Using a DBMS, it can
  efficiently track each product’s stock, sale, and restock in real-time. The
  DBMS can provide quick access to product details, prevent duplicate data (like
  product IDs), and allow multiple users (store staff) to access the database
  simultaneously without interference.
</p>

<!-- <hr class="line-break" /> -->
<h2>4. ACID Properties</h2>
<p>
  The ACID properties are essential for ensuring reliability in DBMS
  transactions. Each property guarantees different aspects of transaction
  safety:
</p>

<table>
  <tr>
    <th>Property</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td>Atomicity</td>
    <td>
      A transaction must complete fully or not at all. If any part of the
      transaction fails, the whole transaction is rolled back.
    </td>
    <td>
      Transferring funds between accounts: if funds are deducted from one
      account, they must be added to the other, or none.
    </td>
  </tr>
  <tr>
    <td>Consistency</td>
    <td>
      Ensures data remains consistent before and after a transaction, enforcing
      all database rules (like constraints and relationships).
    </td>
    <td>
      Prevents data that violates constraints, like trying to insert an order
      for a non-existent product.
    </td>
  </tr>
  <tr>
    <td>Isolation</td>
    <td>
      Transactions are independent of each other. Changes in one transaction
      remain invisible to others until it completes.
    </td>
    <td>Multiple customers adding items to their cart without interference.</td>
  </tr>
  <tr>
    <td>Durability</td>
    <td>
      Once a transaction completes, its result persists even if the system
      crashes.
    </td>
    <td>
      After transferring funds, the final balance is saved permanently,
      unaffected by system failures.
    </td>
  </tr>
</table>

<h3>Example of ACID Properties in SQL</h3>
<pre>
<code>BEGIN TRANSACTION;
UPDATE Accounts SET balance = balance - 500 WHERE account_id = 'Account_A';
UPDATE Accounts SET balance = balance + 500 WHERE account_id = 'Account_B';
COMMIT;
</code>
</pre>
<p>
  If any part of this transaction fails, both updates are rolled back,
  maintaining atomicity.
</p>

<!-- <hr class="line-break" /> -->
<h2>5. Components of DBMS</h2>
<p>
  A DBMS is composed of several components that work together to provide a
  complete data management environment.
</p>

<table>
  <tr>
    <th>Component</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Database Engine</td>
    <td>
      The core service that handles CRUD (Create, Read, Update, Delete)
      operations, data storage, and retrieval.
    </td>
  </tr>
  <tr>
    <td>Query Processor</td>
    <td>
      Interprets and executes SQL queries by translating high-level commands
      into machine-level instructions.
    </td>
  </tr>
  <tr>
    <td>Transaction Manager</td>
    <td>
      Ensures ACID properties by managing transactions and concurrency, handling
      commits and rollbacks.
    </td>
  </tr>
  <tr>
    <td>Storage Manager</td>
    <td>
      Manages data storage and organization on the disk, efficiently accessing
      data blocks.
    </td>
  </tr>
  <tr>
    <td>Metadata Manager</td>
    <td>
      Stores and manages metadata, which is the data about the database’s
      structure, constraints, and relationships.
    </td>
  </tr>
  <tr>
    <td>User Interface</td>
    <td>
      Provides tools like SQL editors or GUIs, enabling users to interact with
      the database.
    </td>
  </tr>
</table>

<h3>Example: How DBMS Components Work Together</h3>
<p>
  Let’s consider a movie rental system where customers can rent and return
  movies. Here’s how each DBMS component plays a role:
</p>
<ul>
  <li>
    <strong>Database Engine</strong> stores all customer data, movie data, and
    rental records.
  </li>
  <li>
    <strong>Query Processor</strong> interprets queries, like retrieving all
    movies available for rent.
  </li>
  <li>
    <strong>Transaction Manager</strong> ensures that if a customer rents
    multiple movies, either all movies are updated in the database as rented, or
    none if there's an error.
  </li>
  <li>
    <strong>Storage Manager</strong> organizes the storage of movie data to
    allow efficient retrieval.
  </li>
  <li>
    <strong>Metadata Manager</strong> maintains metadata on customer
    information, movie categories, and rental durations.
  </li>
  <li>
    <strong>User Interface</strong> allows staff to search for movies, register
    new rentals, and update the movie inventory.
  </li>
</ul>
<br />
<!-- <hr class="line-break" /> -->
<h2>Summary Table: Components and Use in DBMS</h2>
<table>
  <tr>
    <th>Component</th>
    <th>Role in Movie Rental System Example</th>
  </tr>
  <tr>
    <td>Database Engine</td>
    <td>Stores customer data, movie inventory, and rental records</td>
  </tr>
  <tr>
    <td>Query Processor</td>
    <td>
      Executes customer or staff queries to retrieve available movies or due
      rentals
    </td>
  </tr>
  <tr>
    <td>Transaction Manager</td>
    <td>Manages transactions like renting multiple movies at once</td>
  </tr>
  <tr>
    <td>Storage Manager</td>
    <td>Manages how data for each movie, rental, and customer is stored</td>
  </tr>
  <tr>
    <td>Metadata Manager</td>
    <td>
      Stores structural data, like constraints on rental limits or due dates
    </td>
  </tr>
  <tr>
    <td>User Interface</td>
    <td>
      Provides a GUI or query editor for staff to interact with the system
    </td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h3>Practical Example: Sample Tables for Movie Rental System</h3>

<h4>1. Customers Table</h4>
<table>
  <tr>
    <th>customer_id</th>
    <th>name</th>
    <th>contact_info</th>
    <th>membership_level</th>
  </tr>
  <tr>
    <td>101</td>
    <td>John Doe</td>
    <td>john@example.com</td>
    <td>Gold</td>
  </tr>
  <tr>
    <td>102</td>
    <td>Jane Smith</td>
    <td>jane@example.com</td>
    <td>Silver</td>
  </tr>
</table>

<h4>2. Movies Table</h4>
<table>
  <tr>
    <th>movie_id</th>
    <th>title</th>
    <th>genre</th>
    <th>availability</th>
  </tr>
  <tr>
    <td>201</td>
    <td>The Matrix</td>
    <td>Sci-Fi</td>
    <td>Available</td>
  </tr>
  <tr>
    <td>202</td>
    <td>Inception</td>
    <td>Thriller</td>
    <td>Rented</td>
  </tr>
</table>

<h4>3. Rentals Table</h4>
<table>
  <tr>
    <th>rental_id</th>
    <th>customer_id</th>
    <th>movie_id</th>
    <th>rental_date</th>
    <th>return_date</th>
  </tr>
  <tr>
    <td>301</td>
    <td>101</td>
    <td>201</td>
    <td>2024-11-01</td>
    <td>2024-11-07</td>
  </tr>
  <tr>
    <td>302</td>
    <td>102</td>
    <td>202</td>
    <td>2024-11-02</td>
    <td>2024-11-09</td>
  </tr>
</table>

<h3>Sample Query: Retrieve All Movies Available for Rent</h3>
<pre>
<code>SELECT title, genre
FROM Movies
WHERE availability = 'Available';
</code>
</pre>

<p><strong>Output:</strong></p>
<table>
  <tr>
    <th>title</th>
    <th>genre</th>
  </tr>
  <tr>
    <td>The Matrix</td>
    <td>Sci-Fi</td>
  </tr>
</table>

<hr class="line-break" />
<h1>Need, Advantages, and Disadvantages of DBMS</h1>

<h2>Database Applications in Various Fields</h2>
<p>
  Database applications are essential in various sectors due to their ability to
  efficiently manage, retrieve, and analyze data. Let's explore some common uses
  of databases in different fields:
</p>

<h3>1. Banking and Finance</h3>
<p>
  Example: Banks use databases to store customer account information,
  transaction history, and loan records. A customer’s details, account status,
  and transaction history can be quickly retrieved when needed.
</p>

<h4>Schema Example:</h4>
<table>
  <tr>
    <th>AccountID</th>
    <th>CustomerName</th>
    <th>AccountType</th>
    <th>Balance</th>
    <th>LastTransactionDate</th>
  </tr>
  <tr>
    <td>12345</td>
    <td>Alice</td>
    <td>Savings</td>
    <td>$5000</td>
    <td>2024-11-01</td>
  </tr>
  <tr>
    <td>67890</td>
    <td>Bob</td>
    <td>Checking</td>
    <td>$2500</td>
    <td>2024-10-28</td>
  </tr>
</table>

<p>
  <strong>Use Case:</strong> When a customer initiates a transaction, the
  database ensures the account has sufficient balance, deducts the transaction
  amount, and updates the balance in real time.
</p>

<h3>2. Education</h3>
<p>
  Example: Universities and schools use databases to store student records,
  courses, grades, and attendance.
</p>

<h4>Schema Example:</h4>
<table>
  <tr>
    <th>StudentID</th>
    <th>Name</th>
    <th>Course</th>
    <th>Grade</th>
    <th>Attendance</th>
  </tr>
  <tr>
    <td>001</td>
    <td>John Doe</td>
    <td>Math 101</td>
    <td>A</td>
    <td>90%</td>
  </tr>
  <tr>
    <td>002</td>
    <td>Jane Smith</td>
    <td>History 202</td>
    <td>B+</td>
    <td>85%</td>
  </tr>
</table>

<p>
  <strong>Use Case:</strong> When generating report cards, the database
  aggregates each student's grades across different courses.
</p>

<h3>3. E-commerce</h3>
<p>
  Example: E-commerce platforms manage vast amounts of data on products,
  customers, orders, and shipping.
</p>

<h4>Schema Example:</h4>
<table>
  <tr>
    <th>OrderID</th>
    <th>CustomerID</th>
    <th>ProductID</th>
    <th>Quantity</th>
    <th>OrderDate</th>
  </tr>
  <tr>
    <td>1001</td>
    <td>200</td>
    <td>3001</td>
    <td>2</td>
    <td>2024-11-02</td>
  </tr>
  <tr>
    <td>1002</td>
    <td>201</td>
    <td>3005</td>
    <td>1</td>
    <td>2024-11-03</td>
  </tr>
</table>

<p>
  <strong>Use Case:</strong> The database updates stock levels when an order is
  placed and provides recommendations to customers based on their order history.
</p>

<h3>4. Healthcare</h3>
<p>
  Example: Hospitals and clinics use databases to manage patient records,
  appointments, treatment histories, and billing.
</p>

<h4>Schema Example:</h4>
<table>
  <tr>
    <th>PatientID</th>
    <th>Name</th>
    <th>Diagnosis</th>
    <th>TreatmentPlan</th>
    <th>LastVisitDate</th>
  </tr>
  <tr>
    <td>10001</td>
    <td>Clara Brown</td>
    <td>Hypertension</td>
    <td>Medication</td>
    <td>2024-10-22</td>
  </tr>
  <tr>
    <td>10002</td>
    <td>James Green</td>
    <td>Diabetes</td>
    <td>Lifestyle Plan</td>
    <td>2024-10-15</td>
  </tr>
</table>

<p>
  <strong>Use Case:</strong> Doctors can retrieve a patient's complete medical
  history before treatment, ensuring continuity and personalized care.
</p>

<!-- <hr class="line-break" /> -->
<h2>Advantages of DBMS</h2>
<p>
  A Database Management System provides several benefits that enhance data
  handling and improve organizational efficiency.
</p>
<ol>
  <li>
    <strong>Data Integrity and Security</strong><br />
    Explanation: DBMS ensures only authorized users access specific data,
    enhancing security. It also validates data to ensure integrity across all
    tables and fields.<br />
    Example: In a banking DBMS, account details are only accessible by
    authorized employees.
  </li>
  <li>
    <strong>Data Redundancy Reduction</strong><br />
    Explanation: Unlike file systems, a DBMS minimizes data duplication by
    normalizing data.<br />
    Example: Customer information is stored once and used by various departments
    (e.g., billing, support), reducing data redundancy.
  </li>
  <li>
    <strong>Easy Data Retrieval and Querying</strong><br />
    Explanation: Using SQL, users can query databases and retrieve specific
    information quickly.<br />
    Example: A retail company can retrieve monthly sales data using a simple SQL
    query:
    <pre><code>SELECT SUM(SalesAmount) FROM Orders WHERE OrderDate BETWEEN '2024-10-01' AND '2024-10-31';</code></pre>
  </li>
  <li>
    <strong>Improved Data Consistency</strong><br />
    Explanation: DBMS enforces data consistency by making sure updates in one
    place are reflected throughout the database.<br />
    Example: Updating a customer’s phone number in one table updates all linked
    tables where the number is used.
  </li>
  <li>
    <strong>Data Backup and Recovery</strong><br />
    Explanation: Most DBMS systems offer automated backup and recovery options
    to prevent data loss during crashes or other issues.<br />
    Example: Databases are regularly backed up in a hospital system, so patient
    data is recoverable even in case of system failure.
  </li>
  <li>
    <strong>Enhanced Data Sharing and Multi-User Environment</strong><br />
    Explanation: Multiple users can access and modify data concurrently without
    conflict, thanks to transaction management.<br />
    Example: In a collaborative team setting, members can update project records
    simultaneously.
  </li>
</ol>
<br />
<!-- <hr class="line-break" /> -->
<h2>Disadvantages of DBMS</h2>
<p>While DBMS has many advantages, there are some limitations to consider:</p>
<ol>
  <li>
    <strong>Cost of DBMS and Infrastructure</strong><br />
    Explanation: Implementing a DBMS can be expensive due to hardware, software,
    and skilled personnel costs.<br />
    Example: Licensing for enterprise DBMS like Oracle or Microsoft SQL Server
    can be high, making it impractical for small businesses.
  </li>
  <li>
    <strong>Complexity in Setup and Management</strong><br />
    Explanation: A DBMS is complex to set up, requiring a team with expertise in
    data modeling, security, and system management.<br />
    Example: A team in an e-commerce company must continually optimize the
    database for performance, especially as data grows.
  </li>
  <li>
    <strong>Performance Overhead for Small-Scale Applications</strong><br />
    Explanation: For small, straightforward applications, a DBMS may introduce
    unnecessary complexity and slow performance.<br />
    Example: A small retail shop might find it easier to manage inventory in a
    simple spreadsheet rather than a DBMS.
  </li>
  <li>
    <strong>Vulnerability to Data Security Breaches</strong><br />
    Explanation: If not properly secured, a DBMS is vulnerable to breaches,
    potentially exposing sensitive information.<br />
    Example: Data breaches in healthcare databases can lead to compromised
    patient confidentiality.
  </li>
  <li>
    <strong>Regular Maintenance and Upgrades</strong><br />
    Explanation: DBMS systems require ongoing updates and maintenance to fix
    bugs, update features, and ensure data integrity.<br />
    Example: In a financial institution, the database must be maintained
    regularly to comply with new regulatory standards.
  </li>
</ol>
<br />
<!-- <hr class="line-break" /> -->
<h2>Practical Example of Database Use</h2>
<p>
  Suppose a company wants to track customer orders. Here’s how a simple
  relational database schema might look and how SQL queries interact with it.
</p>

<h3>Order Table Schema</h3>
<table>
  <tr>
    <th>OrderID</th>
    <th>CustomerID</th>
    <th>ProductID</th>
    <th>Quantity</th>
    <th>OrderDate</th>
  </tr>
  <tr>
    <td>1001</td>
    <td>200</td>
    <td>3001</td>
    <td>2</td>
    <td>2024-11-02</td>
  </tr>
  <tr>
    <td>1002</td>
    <td>201</td>
    <td>3005</td>
    <td>1</td>
    <td>2024-11-03</td>
  </tr>
</table>

<h3>SQL Query Example</h3>
<p>Retrieve all orders placed after November 1, 2024:</p>
<pre><code>SELECT * FROM Orders WHERE OrderDate > '2024-11-01';</code></pre>

<p><strong>Output:</strong></p>
<table>
  <tr>
    <th>OrderID</th>
    <th>CustomerID</th>
    <th>ProductID</th>
    <th>Quantity</th>
    <th>OrderDate</th>
  </tr>
  <tr>
    <td>1001</td>
    <td>200</td>
    <td>3001</td>
    <td>2</td>
    <td>2024-11-02</td>
  </tr>
  <tr>
    <td>1002</td>
    <td>201</td>
    <td>3005</td>
    <td>1</td>
    <td>2024-11-03</td>
  </tr>
</table>

<p>Calculate total quantity of a product sold in November:</p>
<pre><code>SELECT ProductID, SUM(Quantity) as TotalSold
FROM Orders
WHERE OrderDate BETWEEN '2024-11-01' AND '2024-11-30'
GROUP BY ProductID;
</code></pre>

<br />
<hr class="line-break" />
<h1>Data Abstraction</h1>

<p>
  Data Abstraction is a fundamental concept in Database Management Systems
  (DBMS) that simplifies data handling by hiding complex structures from the
  user and exposing only essential information. Think of data abstraction as a
  way to manage data without revealing all the details, much like how a car's
  user interacts with a steering wheel rather than worrying about the engine
  mechanics.
</p>

<p>
  In DBMS, data abstraction helps developers and users work with databases more
  efficiently by allowing them to focus on the "what" rather than the "how."
</p>

<h2>1. What is Data Abstraction?</h2>
<p>
  Data Abstraction in DBMS refers to the process of hiding the complexity of the
  underlying database system from users and only presenting the essential
  information. The purpose is to make database usage simpler for end-users,
  administrators, and developers by focusing on what data is required instead of
  how it's stored or maintained.
</p>

<h3>Key objectives of data abstraction:</h3>
<ul>
  <li>Simplify the interaction with complex database structures.</li>
  <li>
    Enhance security by hiding sensitive or irrelevant data from specific users.
  </li>
  <li>Improve efficiency by optimizing data retrieval and manipulation.</li>
</ul>
<p>
  For instance, while a user might interact with a "Customer" table to get
  customer details, they do not need to know how these records are stored or
  managed internally.
</p>

<!-- <hr class="line-break" /> -->
<h2>2. Levels of Data Abstraction</h2>
<p>
  Data abstraction in a DBMS is typically divided into three levels: Physical
  Level, Logical Level, and View Level. Each level represents a different
  perspective of the database structure.
</p>
<br />
<img
  src="/3tier-xezfEFdQ.png"
  alt=""
  style="display: block; margin: 0 auto"
/>
<br />
<h3>Physical Level (Internal Level)</h3>
<p>
  <strong>Definition:</strong> The physical level defines how data is stored in
  the database, including data storage methods, indexing, and file organization.
  It focuses on the low-level details of data storage, which are managed by the
  database administrator.
</p>

<p>
  <strong>Purpose:</strong> This level is primarily concerned with optimizing
  storage and retrieval methods.
</p>

<p>
  <strong>Example:</strong> A table named "Employees" might be stored on disk as
  binary files or indexed structures, but these details are hidden from the end
  user.
</p>

<table>
  <tr>
    <th>Attribute</th>
    <th>Storage Type</th>
    <th>Index Type</th>
  </tr>
  <tr>
    <td>Employee_ID</td>
    <td>Integer (4 bytes)</td>
    <td>Primary Key</td>
  </tr>
  <tr>
    <td>Name</td>
    <td>Variable-Length String</td>
    <td>Text</td>
  </tr>
  <tr>
    <td>Salary</td>
    <td>Decimal (8 bytes)</td>
    <td>Indexed</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h3>Logical Level (Conceptual Level)</h3>
<p>
  <strong>Definition:</strong> The logical level defines what data is stored and
  the relationships between them without specifying how they are stored. It
  describes the structure of the database, including tables, columns, and
  relationships.
</p>

<p>
  <strong>Purpose:</strong> This level represents the data as a whole and is
  accessed by developers or database administrators to manage and manipulate the
  database schema.
</p>

<p>
  <strong>Example:</strong> The "Employees" table structure with attributes like
  Employee_ID, Name, Position, and Salary can be accessed and manipulated at the
  logical level, without the need to understand storage details.
</p>

<table>
  <tr>
    <th>Table</th>
    <th>Attributes</th>
  </tr>
  <tr>
    <td>Employees</td>
    <td>Employee_ID, Name, Position, Salary</td>
  </tr>
  <tr>
    <td>Departments</td>
    <td>Department_ID, Department_Name</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h3>View Level (External Level)</h3>
<p>
  <strong>Definition:</strong> The view level is the highest level of data
  abstraction that provides a user-specific view of the data. Users interact
  with data through views that present only relevant data according to their
  needs.
</p>

<p>
  <strong>Purpose:</strong> This level controls access by allowing specific
  views of the data while hiding sensitive or unnecessary information.
</p>

<p>
  <strong>Example:</strong> A view named "Employee_Salary_View" may display only
  the Employee_ID and Salary for payroll staff, hiding other information like
  personal details.
</p>

<table>
  <tr>
    <th>View Name</th>
    <th>Visible Attributes</th>
  </tr>
  <tr>
    <td>Employee_Salary_View</td>
    <td>Employee_ID, Salary</td>
  </tr>
  <tr>
    <td>Employee_Contact_View</td>
    <td>Employee_ID, Name, Contact</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h2>3. Database Schemas</h2>
<p>
  A schema is the blueprint or structure of a database that defines how data is
  organized and related. In DBMS, schemas are categorized based on the level of
  abstraction.
</p>

<h3>Physical Schema</h3>
<p>
  <strong>Definition:</strong> The physical schema defines the physical storage
  structure of the database, including file locations, data compression
  techniques, and indexing mechanisms.
</p>

<p>
  <strong>Purpose:</strong> Physical schemas are used by database administrators
  to manage and optimize storage efficiency.
</p>

<p>
  <strong>Example:</strong> If the "Employees" table is stored in a compressed
  format to save space, this detail would be defined in the physical schema.
</p>

<h3>Logical Schema</h3>
<p>
  <strong>Definition:</strong> The logical schema outlines the structure of the
  entire database, including tables, relationships, constraints, and data types.
</p>

<p>
  <strong>Purpose:</strong> Logical schemas represent the actual data model and
  are used by developers to understand data relationships and constraints.
</p>

<table>
  <tr>
    <th>Entity</th>
    <th>Attribute</th>
    <th>Data Type</th>
    <th>Constraint</th>
  </tr>
  <tr>
    <td>Employees</td>
    <td>Employee_ID</td>
    <td>Integer</td>
    <td>Primary Key</td>
  </tr>
  <tr>
    <td>Employees</td>
    <td>Name</td>
    <td>Varchar(50)</td>
    <td>Not Null</td>
  </tr>
  <tr>
    <td>Departments</td>
    <td>Department_ID</td>
    <td>Integer</td>
    <td>Primary Key</td>
  </tr>
</table>

<h3>External Schema</h3>
<p>
  <strong>Definition:</strong> The external schema, also known as a view schema,
  is a tailored view for end-users that presents data in a way that meets
  specific requirements.
</p>

<p>
  <strong>Purpose:</strong> External schemas provide a customized view for
  different users, controlling access and enhancing usability.
</p>

<p>
  <strong>Example:</strong> An HR view might allow HR personnel to see employee
  details, while a finance view only allows access to payroll information.
</p>

<table>
  <tr>
    <th>External View</th>
    <th>Attributes Visible</th>
  </tr>
  <tr>
    <td>HR View</td>
    <td>Employee_ID, Name, Position, Department</td>
  </tr>
  <tr>
    <td>Payroll View</td>
    <td>Employee_ID, Salary</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->
<h2>4. Database Views</h2>
<p>
  A database view is a virtual table representing a subset of the data from one
  or more tables. Views do not store data physically but act as a lens to
  present data from underlying tables.
</p>

<h3>Purpose of Views</h3>
<ul>
  <li>Simplify complex queries by presenting only necessary information.</li>
  <li>Enhance security by restricting access to specific columns or rows.</li>
  <li>
    Improve readability and usability for users by hiding irrelevant data.
  </li>
</ul>

<h3>Creating a View</h3>
<p>Here’s how a view can be created in SQL:</p>
<pre><code>CREATE VIEW Employee_Salary_View AS
SELECT Employee_ID, Salary
FROM Employees;
</code></pre>

<p>
  In this example, the view Employee_Salary_View only shows Employee_ID and
  Salary, hiding other sensitive information such as the employee's contact
  details.
</p>

<!-- <hr class="line-break" /> -->
<h2>5. Database Instances</h2>
<p>
  A database instance is a specific snapshot of the database at a particular
  moment in time. Unlike schemas, which define the structure, instances contain
  the actual data.
</p>

<h3>Difference Between Schema and Instance</h3>
<table>
  <tr>
    <th>Aspect</th>
    <th>Schema</th>
    <th>Instance</th>
  </tr>
  <tr>
    <td>Definition</td>
    <td>Structure of the database</td>
    <td>Data within the structure</td>
  </tr>
  <tr>
    <td>Persistence</td>
    <td>Permanent</td>
    <td>Temporary (changes over time)</td>
  </tr>
  <tr>
    <td>Example</td>
    <td>Employee_ID, Name, Salary (columns)</td>
    <td>101, John Doe, 50000 (row data)</td>
  </tr>
</table>

<h3>Example of Instances</h3>
<p>
  Consider an Employees table with attributes Employee_ID, Name, Position, and
  Salary. The schema would define these columns, while an instance would contain
  specific data values, as shown below.
</p>

<table>
  <tr>
    <th>Employee_ID</th>
    <th>Name</th>
    <th>Position</th>
    <th>Salary</th>
  </tr>
  <tr>
    <td>101</td>
    <td>John Doe</td>
    <td>Manager</td>
    <td>80000</td>
  </tr>
  <tr>
    <td>102</td>
    <td>Jane Smith</td>
    <td>Developer</td>
    <td>60000</td>
  </tr>
</table>

<h2>Practical Use Case of Data Abstraction in DBMS</h2>
<p>
  <strong>Use Case:</strong> Imagine an e-commerce platform managing customer,
  order, and product data.
</p>
<ul>
  <li>
    <strong>Physical Level:</strong> Data on customer details, orders, and
    products are stored as binary files with specific indexing for fast
    retrieval.
  </li>
  <li>
    <strong>Logical Level:</strong> Relationships between Customer, Order, and
    Product tables are defined, such as foreign key constraints linking orders
    to customers and products.
  </li>
  <li>
    <strong>View Level:</strong> The platform's customer service team might have
    a view that only displays customer and order data, while the product
    management team sees views containing product information.
  </li>
</ul>
<br />
<!-- <hr class="line-break" /> -->
<h3>Example: Library Database</h3>
<p>
  Consider a library database that manages data on Books, Authors, and
  Borrowers. This example shows how data is stored and presented at each level
  of abstraction.
</p>

<h3>1. Physical Level (Internal Level)</h3>
<p>
  At the physical level, the database administrator decides how data is stored
  on the disk. For example:
</p>
<ul>
  <li>
    The Books table is stored as a binary file, with specific indexing on the
    ISBN column for fast access.
  </li>
  <li>The Borrowers table is compressed to save storage space.</li>
</ul>

<table>
  <tr>
    <th>Table</th>
    <th>File Type</th>
    <th>Storage Type</th>
    <th>Indexing Method</th>
  </tr>
  <tr>
    <td>Books</td>
    <td>Binary</td>
    <td>Compressed</td>
    <td>Indexed on ISBN</td>
  </tr>
  <tr>
    <td>Authors</td>
    <td>Text File</td>
    <td>Not Compressed</td>
    <td>Not Indexed</td>
  </tr>
  <tr>
    <td>Borrowers</td>
    <td>Binary</td>
    <td>Compressed</td>
    <td>Indexed on ID</td>
  </tr>
</table>

<h3>2. Logical Level (Conceptual Level)</h3>
<p>
  At the logical level, the structure of the data is defined, including table
  names, columns, data types, and relationships.
</p>

<table>
  <tr>
    <th>Table</th>
    <th>Attributes</th>
    <th>Data Type</th>
    <th>Constraints</th>
  </tr>
  <tr>
    <td>Books</td>
    <td>ISBN, Title, Author_ID, Copies</td>
    <td>Integer, Varchar, Integer</td>
    <td>Primary Key: ISBN, Foreign Key: Author_ID</td>
  </tr>
  <tr>
    <td>Authors</td>
    <td>Author_ID, Name, Country</td>
    <td>Integer, Varchar</td>
    <td>Primary Key: Author_ID</td>
  </tr>
  <tr>
    <td>Borrowers</td>
    <td>Borrower_ID, Name, Email</td>
    <td>Integer, Varchar</td>
    <td>Primary Key: Borrower_ID</td>
  </tr>
  <tr>
    <td>BorrowedBooks</td>
    <td>Borrower_ID, ISBN, DueDate</td>
    <td>Integer, Integer, Date</td>
    <td>Foreign Keys: Borrower_ID, ISBN</td>
  </tr>
</table>

<h3>3. View Level (External Level)</h3>
<p>At the view level, users only see the data that is relevant to them.</p>

<h4>Librarian View</h4>
<pre><code>CREATE VIEW Librarian_View AS
SELECT Books.ISBN, Books.Title, Authors.Name AS Author, Borrowers.Name AS Borrower, BorrowedBooks.DueDate
FROM Books
JOIN Authors ON Books.Author_ID = Authors.Author_ID
LEFT JOIN BorrowedBooks ON Books.ISBN = BorrowedBooks.ISBN
LEFT JOIN Borrowers ON BorrowedBooks.Borrower_ID = Borrowers.Borrower_ID;
</code></pre>

<table>
  <tr>
    <th>ISBN</th>
    <th>Title</th>
    <th>Author</th>
    <th>Borrower</th>
    <th>DueDate</th>
  </tr>
  <tr>
    <td>12345</td>
    <td>Database Systems</td>
    <td>C.J. Date</td>
    <td>Alice Johnson</td>
    <td>2024-11-10</td>
  </tr>
  <tr>
    <td>67890</td>
    <td>Data Abstraction</td>
    <td>John Doe</td>
    <td>NULL</td>
    <td>NULL</td>
  </tr>
</table>

<h4>Borrower View</h4>
<pre><code>CREATE VIEW Borrower_View AS
SELECT BorrowedBooks.ISBN, Books.Title, BorrowedBooks.DueDate
FROM BorrowedBooks
JOIN Books ON BorrowedBooks.ISBN = Books.ISBN
WHERE BorrowedBooks.Borrower_ID = CURRENT_USER_ID;
</code></pre>

<table>
  <tr>
    <th>ISBN</th>
    <th>Title</th>
    <th>DueDate</th>
  </tr>
  <tr>
    <td>12345</td>
    <td>Database Systems</td>
    <td>2024-11-10</td>
  </tr>
</table>

<hr class="line-break" />
<h1>DBMS Architecture</h1>

<p>
  Database Management System (DBMS) architecture refers to the layers and
  components that make up the system, defining how it stores, manages, and
  interacts with data. Different architectures, such as 1-Tier, 2-Tier, and
  3-Tier, define the layout of the system based on its usage, scalability, and
  complexity needs. Each architecture type has its unique strengths, making it
  suitable for various applications and environments.
</p>

<!-- <hr class="line-break" /> -->
<h2>1. 1-Tier Architecture</h2>
<p>
  In a 1-Tier Architecture, the database and the user interface are both located
  on the same machine, making it the simplest DBMS structure. Here, the user
  directly interacts with the database, often through command-line or user
  interface applications, to perform operations.
</p>

<img
  src="/1tier-283W7e8c.png"
  alt=""
  style="display: block; margin: 0 auto"
/>

<h3>Characteristics of 1-Tier Architecture</h3>
<ul>
  <li>Direct interaction with the database.</li>
  <li>
    All components (data storage, processing, and user interface) reside on a
    single machine.
  </li>
  <li>
    Primarily used by developers for local databases or single-user
    applications.
  </li>
</ul>

<h3>Use Cases of 1-Tier Architecture</h3>
<ul>
  <li>
    <strong>Development and Testing:</strong> Often used in environments where
    developers need to test database functionality.
  </li>
  <li>
    <strong>Personal Databases:</strong> Suitable for small applications like
    single-user databases or personal data management systems (e.g., SQLite).
  </li>
</ul>

<p>
  <strong>Example of 1-Tier Architecture:</strong> Consider a student project
  where a developer sets up a local database on their laptop to manage course
  materials and schedules. The database, UI, and data processing all occur on
  the same system, making it easy to develop and test without additional
  configuration.
</p>

<pre><code>CREATE TABLE Courses (
    Course_ID INTEGER PRIMARY KEY,
    Course_Name TEXT NOT NULL,
    Instructor TEXT
);

INSERT INTO Courses (Course_ID, Course_Name, Instructor)
VALUES (1, 'Database Systems', 'Dr. Smith');
</code></pre>

<h3>Advantages and Disadvantages of 1-Tier Architecture</h3>
<table>
  <tr>
    <th>Advantages</th>
    <th>Disadvantages</th>
  </tr>
  <tr>
    <td>Easy to set up and maintain</td>
    <td>Limited scalability</td>
  </tr>
  <tr>
    <td>Fast for single-user applications</td>
    <td>Not suitable for multi-user environments</td>
  </tr>
  <tr>
    <td>Minimal networking requirements</td>
    <td>No data abstraction from end-users</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->

<h2>2. 2-Tier Architecture</h2>
<p>
  In 2-Tier Architecture, the DBMS and the application layer are separated. The
  client (user interface) communicates directly with the server (DBMS) over a
  network. This architecture introduces a client-server model where the client
  sends requests to the server, and the server processes these requests and
  returns the results.
</p>

<img
  src="/2tier-izgfIzec.png"
  alt=""
  style="display: block; margin: 0 auto"
/>

<h3>Characteristics of 2-Tier Architecture</h3>
<ul>
  <li>Separation of user interface and database management.</li>
  <li>Direct communication between client and server.</li>
  <li>
    Common in applications that require multi-user access but have minimal
    interaction with additional layers.
  </li>
</ul>

<h3>Use Cases of 2-Tier Architecture</h3>
<ul>
  <li>
    <strong>Small and Medium-sized Applications:</strong> Suitable for systems
    where a limited number of users require concurrent access to the database,
    such as in departmental applications or internal company tools.
  </li>
  <li>
    <strong>Database-driven Applications:</strong> Common in applications where
    clients need to interact with a central database over a network, like a
    university library system.
  </li>
</ul>

<p>
  <strong>Example of 2-Tier Architecture:</strong> In a university library
  system, the client application (on a librarian’s workstation) connects
  directly to a central database server that holds information about books,
  borrowers, and transaction history. The client application sends queries to
  the server, which processes them and returns results.
</p>

<pre><code>SELECT Book_ID, Title, Borrower_Name, Due_Date
FROM Borrowed_Books
WHERE Borrower_Name = 'Alice Johnson';
</code></pre>

<h3>Advantages and Disadvantages of 2-Tier Architecture</h3>
<table>
  <tr>
    <th>Advantages</th>
    <th>Disadvantages</th>
  </tr>
  <tr>
    <td>Allows multiple users to access the database</td>
    <td>Limited scalability and flexibility</td>
  </tr>
  <tr>
    <td>More secure and organized than 1-Tier</td>
    <td>Changes on the server require client updates</td>
  </tr>
  <tr>
    <td>Suitable for small to medium applications</td>
    <td>Direct dependency on server availability</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->

<h2>3. 3-Tier Architecture</h2>
<p>
  3-Tier Architecture is the most complex and scalable DBMS architecture, adding
  a middle layer (application server) between the client and the database
  server. This layer, known as the application server or middleware, handles
  business logic, processes requests, and communicates between the client and
  the database server.
</p>

<img
  src="/3tier-ZAgb0QOu.png"
  alt=""
  style="display: block; margin: 0 auto"
/>

<h3>Characteristics of 3-Tier Architecture</h3>
<ul>
  <li>
    Adds a middle layer between the client and database to manage requests and
    business logic.
  </li>
  <li>
    Clients interact with the application server, which then communicates with
    the database.
  </li>
  <li>
    Commonly used in web-based applications and large enterprise systems, where
    scalability, security, and data abstraction are critical.
  </li>
</ul>

<h3>Use Cases of 3-Tier Architecture</h3>
<ul>
  <li>
    <strong>Web Applications:</strong> Ideal for online platforms, where users
    access the application over the internet.
  </li>
  <li>
    <strong>Enterprise Systems:</strong> Common in large organizations, allowing
    scalability, security, and high availability.
  </li>
</ul>

<p>
  <strong>Example of 3-Tier Architecture:</strong> An e-commerce application
  where users browse products, add items to their cart, and complete
  transactions demonstrates 3-tier architecture. Here’s a breakdown of the flow:
</p>
<ul>
  <li>
    <strong>Client Layer:</strong> The user interacts with the web browser to
    browse products.
  </li>
  <li>
    <strong>Application Layer:</strong> The application server processes user
    actions like adding items to the cart, managing inventory, and processing
    payments.
  </li>
  <li>
    <strong>Database Layer:</strong> The database server stores all data related
    to products, orders, users, and inventory.
  </li>
</ul>

<p>
  In this example, the application server acts as a middleman, handling user
  requests and sending necessary queries to the database.
</p>

<pre><code>SELECT Product_ID, Product_Name, Price, Stock
FROM Products
WHERE Category = 'Electronics';
</code></pre>

<h3>Advantages and Disadvantages of 3-Tier Architecture</h3>
<table>
  <tr>
    <th>Advantages</th>
    <th>Disadvantages</th>
  </tr>
  <tr>
    <td>Highly scalable, flexible, and secure</td>
    <td>More complex to develop and maintain</td>
  </tr>
  <tr>
    <td>Suitable for high-traffic applications</td>
    <td>Increased costs and resource requirements</td>
  </tr>
  <tr>
    <td>Business logic and data handling are separate</td>
    <td>Potential delays due to middleware processing</td>
  </tr>
  <tr>
    <td>Independent updates to each layer possible</td>
    <td>Requires efficient network management</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->

<h2>Comparison of 1-Tier, 2-Tier, and 3-Tier Architectures</h2>
<table>
  <tr>
    <th>Feature</th>
    <th>1-Tier</th>
    <th>2-Tier</th>
    <th>3-Tier</th>
  </tr>
  <tr>
    <td>Layers</td>
    <td>Single layer</td>
    <td>Client & Server</td>
    <td>Client, Application, & Server</td>
  </tr>
  <tr>
    <td>Complexity</td>
    <td>Low</td>
    <td>Medium</td>
    <td>High</td>
  </tr>
  <tr>
    <td>Scalability</td>
    <td>Limited</td>
    <td>Moderate</td>
    <td>High</td>
  </tr>
  <tr>
    <td>Data Security</td>
    <td>Low</td>
    <td>Medium</td>
    <td>High</td>
  </tr>
  <tr>
    <td>Use Case</td>
    <td>Single-user applications</td>
    <td>Small to medium applications</td>
    <td>Large enterprise applications</td>
  </tr>
  <tr>
    <td>Example</td>
    <td>Local database for testing</td>
    <td>University library system</td>
    <td>E-commerce platform</td>
  </tr>
</table>

<!-- <hr class="line-break" /> -->

<h2>Conclusion</h2>
<p>
  The architecture of a DBMS affects its scalability, security, and performance.
  Choosing the right architecture depends on the application’s size, complexity,
  and user requirements:
</p>
<ul>
  <li>1-Tier is ideal for personal databases or development environments.</li>
  <li>
    2-Tier suits small to medium-sized applications where direct interaction
    with a central database is needed.
  </li>
  <li>
    3-Tier is best for large-scale applications that require high security,
    scalability, and data abstraction.
  </li>
</ul>
<br />
<hr class="line-break" />
<h1>Types of Database Users and Their Roles</h1>

<p>
  Database users are individuals or systems that interact with a database for
  different purposes, ranging from administration and programming to analysis
  and query execution. Each user type has distinct roles and responsibilities
  based on their interaction level and use case.
</p>

<h2>1. Database Administrator (DBA)</h2>
<p>
  The Database Administrator (DBA) is responsible for managing and maintaining
  the database system, ensuring data integrity, security, and optimal
  performance.
</p>

<h3>Roles and Responsibilities</h3>
<ul>
  <li>
    <strong>Database Maintenance:</strong> Regularly backing up and restoring
    data.
  </li>
  <li>
    <strong>Performance Tuning:</strong> Optimizing query performance and system
    efficiency.
  </li>
  <li>
    <strong>User Management:</strong> Creating, updating, and managing user
    access.
  </li>
  <li>
    <strong>Security Management:</strong> Ensuring data protection through
    access controls and encryption.
  </li>
  <li>
    <strong>Troubleshooting:</strong> Resolving issues like system crashes or
    data corruption.
  </li>
</ul>

<h4>Real-Life Relation</h4>
<p>
  In a banking system, a DBA ensures that customer transaction data is secure,
  accessible, and backed up.
</p>
<!-- <hr class="line-break" /> -->
<h2>2. End Users</h2>
<p>
  End users are individuals who interact with the database indirectly through
  applications. They perform tasks like querying or updating records, often
  without technical knowledge of the database system.
</p>

<h3>Types of End Users</h3>
<ul>
  <li>
    <strong>Casual Users:</strong> Occasionally retrieve or update data, such as
    managers viewing reports.
  </li>
  <li>
    <strong>Naive Users:</strong> Perform predefined operations via
    applications, like booking tickets on a website.
  </li>
  <li>
    <strong>Power Users:</strong> Use advanced tools to extract complex
    insights, such as business analysts.
  </li>
</ul>

<h4>Real-Life Relation</h4>
<p>
  A customer querying their account balance via a banking app is an end user.
</p>
<!-- <hr class="line-break" /> -->
<h2>3. Application Programmers</h2>
<p>
  Application programmers design and develop software applications that interact
  with the database. They write code to execute queries, manage transactions,
  and present data to end users.
</p>

<h3>Roles and Responsibilities</h3>
<ul>
  <li><strong>Writing efficient queries:</strong> Using SQL or APIs.</li>
  <li>
    <strong>Ensuring smooth database integration:</strong> Within applications.
  </li>
  <li>
    <strong>Implementing data validation rules:</strong> Within applications.
  </li>
</ul>

<h4>Real-Life Relation</h4>
<p>
  An e-commerce platform's developer codes the application to fetch product data
  from a database and display it to users.
</p>
<!-- <hr class="line-break" /> -->
<h2>4. System Analysts</h2>
<p>
  System analysts bridge the gap between business requirements and technical
  implementation. They analyze user needs, design database schemas, and ensure
  the database aligns with organizational goals.
</p>

<h3>Roles and Responsibilities</h3>
<ul>
  <li>
    <strong>Identifying database requirements:</strong> Based on user needs.
  </li>
  <li>
    <strong>Designing logical data models and schemas:</strong> To meet
    organizational goals.
  </li>
  <li>
    <strong>Collaborating with DBAs and developers:</strong> To implement
    solutions.
  </li>
</ul>

<h4>Real-Life Relation</h4>
<p>
  In a retail company, a system analyst might design a schema to handle
  inventory and sales data based on business needs.
</p>
<!-- <hr class="line-break" /> -->
<h2>5. Data Scientists and Analysts</h2>
<p>
  Data scientists and analysts use databases to extract meaningful insights,
  often working with structured and unstructured data to support
  decision-making.
</p>

<h3>Roles and Responsibilities</h3>
<ul>
  <li><strong>Extracting and cleaning data:</strong> From databases.</li>
  <li>
    <strong>Analyzing data:</strong> Using statistical or machine learning
    models.
  </li>
  <li>
    <strong>Creating visualizations and reports:</strong> To convey insights.
  </li>
</ul>

<h4>Real-Life Relation</h4>
<p>
  A data scientist analyzing customer purchase patterns from a retail database
  to optimize marketing strategies.
</p>

<!-- <hr class="line-break" /> -->
<h2>Comparison Table</h2>
<table>
  <tr>
    <th>User Type</th>
    <th>Primary Role</th>
    <th>Examples of Tasks</th>
    <th>Expertise Level</th>
  </tr>
  <tr>
    <td>Database Administrator</td>
    <td>Manage and maintain the database</td>
    <td>Backups, performance tuning</td>
    <td>High</td>
  </tr>
  <tr>
    <td>End Users</td>
    <td>Interact with the database indirectly</td>
    <td>Query account balance, book tickets</td>
    <td>Low to Moderate</td>
  </tr>
  <tr>
    <td>Application Programmers</td>
    <td>Develop database-driven applications</td>
    <td>Write queries, manage transactions</td>
    <td>High</td>
  </tr>
  <tr>
    <td>System Analysts</td>
    <td>Bridge business and technical needs</td>
    <td>Design schemas, analyze requirements</td>
    <td>Moderate to High</td>
  </tr>
  <tr>
    <td>Data Scientists</td>
    <td>Extract insights from data</td>
    <td>Data cleaning, visualization</td>
    <td>High</td>
  </tr>
</table>
<br />
<!-- <hr class="line-break" /> -->
