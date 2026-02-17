<!-- AUTHOR: Reece Hannah -->
<!-- CREATED: December 2025 -->
<!-- VERSION: 2.0.0 -->

# 🎓 Algonquin College Student Dashboard

**Version:** 2.0.0 | **Last Updated:** December 2025 | **Author:** Reece Hannah

<div align="center">
  
[![Algonquin College](https://img.shields.io/badge/Algonquin%20College-Official-00703c?style=for-the-badge)](https://www.algonquincollege.com)
[![Brightspace](https://img.shields.io/badge/Brightspace-Integrated-006fbf?style=for-the-badge)](https://brightspace.algonquincollege.com)
[![Student Dashboard](https://img.shields.io/badge/Student-Dashboard-9d1fd4?style=for-the-badge)]()
  
</div>

---

## 📋 Quick Navigation

<details>
<summary><strong>📑 Click to expand table of contents</strong></summary>

- [Overview](#-overview)
- [Features](#-features)
- [Technology Stack](#-technology-stack)
- [Installation](#-installation)
- [Usage Guide](#-usage-guide)
- [Component Library](#-component-library)
- [API Integration](#-api-integration)
- [Configuration](#-configuration)
- [Performance Metrics](#-performance-metrics)
- [Browser Support](#-browser-support)
- [Accessibility](#-accessibility)
- [Contributing](#-contributing)
- [Version History](#-version-history)
- [License](#-license)

</details>

---

## 🎯 Overview

The **Algonquin College Student Dashboard** is a comprehensive, fully-featured web application designed specifically for Algonquin College students. Created by **Reece Hannah**, this dashboard serves as a centralized hub for managing academic life, providing seamless access to courses, calendars, notifications, and essential college resources.

### 🏆 Key Highlights

| Feature | Description | Status |
|---------|-------------|--------|
| 👤 **Personalized Experience** | Tailored dashboard for student Reece Hannah | ✅ Active |
| ⏰ **Real-time Updates** | Live clock, dynamic course loading, session management | ✅ Active |
| 📱 **Responsive Design** | Fully optimized for all devices | ✅ Active |
| 🌙 **Dark Mode Support** | Automatic theme switching | ✅ Active |
| ♿ **Accessibility First** | WCAG 2.1 compliant | ✅ Active |

---

## ✨ Features

### 📚 Core Functionality

<summary><strong>Course Management System</strong></summary>

```javascript
// Sample course data structure
const courses = [
  {
    code: "CST8102",
    title: "Operating System Fundamentals",
    instructor: "Prof. Johnson",
    progress: 75,
    color: "#00703c",
    link: "/d2l/le/content/6837/Home"
  },
  {
    code: "CST8284",
    title: "Object Oriented Programming", 
    instructor: "Dr. Smith",
    progress: 90,
    color: "#006fbf",
    link: "/d2l/le/content/6840/Home"
  },
  {
    code: "MAT8001C",
    title: "Technical Mathematics",
    instructor: "Prof. Chen", 
    progress: 60,
    color: "#9d1fd4",
    link: "/d2l/le/content/6842/Home"
  },
  {
    code: "ENL1813T",
    title: "Communications I",
    instructor: "Prof. Williams",
    progress: 85,
    color: "#d40067",
    link: "/d2l/le/content/6845/Home"
  },
  {
    code: "CST2355",
    title: "Database Systems",
    instructor: "Dr. Martinez",
    progress: 45,
    color: "#cd2026",
    link: "/d2l/le/content/6848/Home"
  },
  {
    code: "GED5001",
    title: "General Education Elective",
    instructor: "Prof. Brown",
    progress: 100,
    color: "#e87511",
    link: "/d2l/le/content/6850/Home"
  }
];

// Course access tracking
function trackCourseAccess(courseName) {
  const accessTime = new Date().toISOString();
  const accessHistory = JSON.parse(localStorage.getItem('courseAccessHistory') || '[]');
  
  accessHistory.unshift({
    course: courseName,
    time: accessTime,
    studentId: '218262'
  });
  
  localStorage.setItem('courseAccessHistory', 
    JSON.stringify(accessHistory.slice(0, 10)));
}

// Load courses with progress indicators
function loadCourses() {
  const coursesContainer = document.getElementById('courses-container');
  
  coursesContainer.innerHTML = courses.map(course => `
    <a href="${course.link}" class="course-card" target="_blank">
      <div class="course-image" style="background: linear-gradient(135deg, ${course.color}20, ${course.color}40);">
        📖
      </div>
      <div class="course-info">
        <h3>${course.code}: ${course.title}</h3>
        <div class="course-meta">
          <span>👨‍🏫 ${course.instructor}</span>
          <span>📊 ${course.progress}%</span>
        </div>
        <div class="course-progress">
          <div class="progress-bar">
            <div class="progress-fill" style="width: ${course.progress}%; background: ${course.color};"></div>
          </div>
          <small>Progress: ${course.progress}% complete</small>
        </div>
      </div>
    </a>
  `).join('');
  
  document.querySelectorAll('.course-card').forEach(card => {
    card.addEventListener('click', function() {
      const courseName = this.querySelector('h3').textContent;
      trackCourseAccess(courseName);
    });
  });
}