# OAS - Online Application System

An online graduate application management system based on PHP and MySQL, supporting student applications, admission officer reviews, and administrator management functions.

## Project Overview

OAS (Online Application System) is a complete online application platform that allows students to browse universities and graduate programs, submit applications, upload relevant documents, while providing corresponding management functions for admission officers and administrators.

## Main Features

### Student Features
- Browse universities and graduate programs
- Filter programs by category and degree type
- Submit applications
- View application status (Pending/Approved/Rejected)
- Upload certificates, transcripts, and other documents (supports PDF, DOC, DOCX, ZIP)
- Manage personal information (basic info, educational background, language scores, etc.)
- Withdraw applications
<img width="3068" height="1702" alt="image" src="https://github.com/user-attachments/assets/41ed6fd9-5d9b-49e9-a0d0-0d0ae7a4b9ba" />
<img width="3065" height="1738" alt="image" src="https://github.com/user-attachments/assets/10134aad-c6a0-45f5-b3be-6f6488043baa" />
<img width="3026" height="1712" alt="image" src="https://github.com/user-attachments/assets/58fd7155-06a2-4f85-8607-60ce736812c2" />
<img width="3010" height="1765" alt="image" src="https://github.com/user-attachments/assets/8f0e479c-45e2-4ca8-9605-ccec8de7576b" />
<img width="3090" height="1062" alt="image" src="https://github.com/user-attachments/assets/2c3c1bad-2e66-4a6a-ba7c-d91a7c6b7967" />

### Admission Officer Features
- View all programs for assigned universities
- View student application lists
- Review applications (approve/reject)
- View student detailed information (GPA, TOEFL, IELTS scores, etc.)
- Download student uploaded files (individual or batch ZIP)
<img width="3051" height="1721" alt="image" src="https://github.com/user-attachments/assets/e855d908-e0b4-456c-81cb-926ca7c95ba1" />

### Administrator Features
- Manage university information (CRUD operations)
- Manage program information (CRUD operations)
- Manage admission officer accounts
- Review admission officer registration applications
- View all application statistics
<img width="3081" height="1741" alt="image" src="https://github.com/user-attachments/assets/f72786eb-3c29-458d-9d17-b656fa3dab26" />


## Project Structure

```
oas/
├── api/                          # API endpoints directory
│   ├── accept_officer_application.php
│   ├── add_program.php
│   ├── add_university.php
│   ├── change_password.php
│   ├── config.php                # API configuration and common functions
│   ├── delete_officer.php
│   ├── delete_program.php
│   ├── delete_student_file.php
│   ├── delete_university.php
│   ├── download_student_file.php
│   ├── download_student_files_zip.php
│   ├── get_applications.php
│   ├── get_officer_applications.php
│   ├── get_officers.php
│   ├── get_operator_applications.php
│   ├── get_operator_programs.php
│   ├── get_programs.php
│   ├── get_public_programs.php
│   ├── get_public_schools.php
│   ├── get_student_files.php
│   ├── get_universities.php
│   ├── reject_officer_application.php
│   ├── update_application_status.php
│   ├── update_program.php
│   ├── update_student_application_status.php
│   ├── update_university.php
│   └── upload_student_file.php
│
├── CSS/                          # Stylesheet files
│   ├── admin.css
│   ├── login.css
│   ├── My_applications.css
│   ├── nav.css
│   ├── profile.css
│   ├── profile2.css
│   ├── program.css
│   ├── rg.css
│   └── school.css
│
├── JS/                           # JavaScript files
│   ├── admin.js
│   ├── login.js
│   ├── officer.js
│   ├── profile.js
│   ├── profile2.js
│   ├── program.js
│   ├── rg.js
│   └── school.js
│
├── sql/                          # Database files
│   └── OAS.sql
│
├── logo/                         # University logo images
│   ├── CMU.png
│   ├── HKU.png
│   ├── HKUST.png
│   ├── MIT.png
│   ├── NTU.png
│   ├── NUS.png
│   ├── Oxford.png
│   ├── stanford.png
│   └── Tsinghua.png
│
├── pic/                          # Other image resources
│   └── Cover.jpg
│
├── uploads/                      # Student uploaded files storage
│   └── students/
│       └── [student_id]/
│
├── test_picture/                 # Test files (can be deleted)
│
├── .htaccess                     # Apache configuration
│
├── index.php                     # Entry file (routing)
├── index.html                    # Static homepage (deprecated)
├── index_student.php             # Student homepage
│
├── login_.php                    # Login page
├── login.php                     # Login handler
├── logout.php                    # Logout handler
├── rg.php                        # Registration page
├── register.php                  # Registration handler
│
├── admin.php                     # Administrator panel
├── officer_dashboard.php         # Admission officer dashboard
│
├── school.php                    # University list page
├── program.php                   # Program list page
├── apply.php                     # Application handler
├── withdraw.php                  # Withdraw application
│
├── profile.php                   # Personal information page (old version)
├── profile2.php                  # Personal information page (new version)
├── change_password.php           # Change password page
│
├── My_applications.php          # My applications list
│
├── basic.php                     # Basic information editor
├── education.php                 # Educational background editor
├── TOEFL.php                     # TOEFL score editor
├── IELTS.php                     # IELTS score editor
│
├── get_image.php                 # Get image (university logo)
│
├── connect.php                   # Database connection configuration
│
└── README.md                     # This file
```

## Database Structure

### Main Tables

- **profile**: User basic information (students, admission officers, administrators)
- **student**: Student detailed information
- **school**: University information
- **program**: Graduate programs (composite primary key: sid + pid)
- **apply**: Application records
- **operator_school**: Relationship between admission officers and schools
- **admin_applications**: Admission officer registration applications
- **files**: File records
- **student_files**: Student file associations
- **language_grade**: Language scores (TOEFL/IELTS)
- **undergraduate**: Undergraduate information
- **region**: Region information

### Key Relationships

- The `program` table uses a composite primary key `(sid, pid)`, where each program belongs to a specific university
- The `operator_school` table manages the relationship between admission officers and schools (one officer can manage all programs of one school)
- The `apply` table records student applications, containing unique identifier `(ID, sid, pid)`

## User Roles

### 1. Student
- Default registration type
- Can browse and apply for programs
- Can upload and manage personal files
- Can view application status

### 2. Admission Officer (operator/officer)
- Requires administrator approval for registration
- Manages all programs for assigned universities
- Reviews student applications
- Downloads student files

### 3. Administrator (admin)
- Highest privileges
- Manages all universities and programs
- Manages admission officer accounts
- Reviews admission officer registration applications


### Installation Steps

1. **Clone or download the project to XAMPP's htdocs directory**
   ```
   C:\xampp\htdocs\oas\
   ```

2. **Configure database connection**
   Edit `connect.php`:
   ```php
   $severname = "localhost";
   $username = "root";
   $password = "";  // Modify according to your setup
   $dbname = "test";  // Modify according to your setup
   ```

3. **Import database**
   - Create database in phpMyAdmin
   - Import `sql/OAS.sql` file

4. **Configure Apache**
   - Ensure `.htaccess` file exists
   - Ensure `mod_rewrite` and `mod_headers` are enabled

5. **Set file upload permissions**
   - Ensure `uploads/` directory is writable
   - Recommended permissions: `chmod 755 uploads`

6. **Access the system**
   - Open browser and visit: `http://localhost/oas/`
   - System will automatically redirect to login page

## Default Configuration

### Database
- Database name: `test` (can be modified in `connect.php`)
- Character set: `utf8mb4`

### File Upload
- Maximum file size: 50MB
- Allowed file types: PDF, DOC, DOCX, ZIP
- Storage path: `uploads/students/{student_id}/`

### Session Configuration
- Session is used for user authentication and state management
- Session is automatically cleared after logout and redirects to login page

## API Endpoints

### Administrator API (requires admin privileges via `api/config.php`)

- `GET api/get_universities.php` - Get all universities
- `GET api/get_programs.php` - Get all programs
- `GET api/get_officers.php` - Get all admission officers
- `GET api/get_officer_applications.php` - Get officer applications
- `POST api/add_university.php` - Add university
- `POST api/update_university.php` - Update university
- `POST api/delete_university.php` - Delete university
- `POST api/add_program.php` - Add program
- `POST api/update_program.php` - Update program
- `POST api/delete_program.php` - Delete program
- `POST api/accept_officer_application.php` - Approve officer application
- `POST api/reject_officer_application.php` - Reject officer application
- `POST api/delete_officer.php` - Delete officer
- `POST api/change_password.php` - Change password

### Admission Officer API

- `GET api/get_operator_programs.php` - Get managed program list
- `GET api/get_operator_applications.php` - Get application list
- `POST api/update_application_status.php` - Update application status
- `GET api/get_student_files.php` - Get student file list
- `GET api/download_student_file.php?fid={fid}` - Download single file
- `GET api/download_student_files_zip.php?studentId={id}` - Download all files (ZIP)

### Student API

- `GET api/get_public_schools.php` - Get public university list
- `GET api/get_public_programs.php?sid={sid}` - Get public program list
- `POST api/upload_student_file.php` - Upload file
- `GET api/get_student_files.php` - Get own file list
- `POST api/delete_student_file.php` - Delete own file
- `POST api/change_password.php` - Change password

## Main Pages

### Student Pages
- `index_student.php` - Student homepage
- `school.php` - University list (with filters)
- `program.php` - Program list (with filters and search)
- `profile2.php` - Personal information management (multi-tab)
- `My_applications.php` - My applications list

### Admission Officer Pages
- `officer_dashboard.php` - Admission officer dashboard
  - Pending applications
  - Approved applications
  - Rejected applications

### Administrator Pages
- `admin.php` - Administrator panel
  - University management
  - Program management
  - Officer management
  - Officer application review

## Features

### Filtering and Search
- **University page**: Filter by country/region
- **Program page**:
  - Filter by category (Area of Interest)
  - Filter by degree type (Master/MBA/PhD)
  - Search by program name

### File Management
- Drag and drop upload support
- ZIP batch upload support
- Officers can batch download student files
- File type validation and size limits

### Performance Monitoring
- `program.php` page displays query performance
- Real-time display of query time and page load time

### Cache Control
- All pages have cache control headers
- Prevents browser caching issues
- Session automatically cleared after logout

## Tech Stack

- **Backend**: PHP 7.0+, MySQL
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Styling**: Custom CSS, Font Awesome icons
- **Architecture**: Traditional MVC pattern, RESTful API

## Important Notes

1. **Database Security**
   - Change default database password in production
   - Use prepared statements to prevent SQL injection

2. **File Upload Security**
   - File type validation implemented
   - Recommend adding virus scanning functionality

3. **Session Security**
   - Ensure session configuration is secure
   - Recommend using HTTPS in production

4. **Path Issues**
   - API files use relative paths `../connect.php`
   - Ensure paths are correct

## License

This project is a course project (Database Management Systems, Section 1003), developed by Group11.

## Development Team

- **Course**: Database Management Systems
- **Section**: 1003
- **Instructor**: Dr. Tianhui MENG

- **Development Group**: Group11
