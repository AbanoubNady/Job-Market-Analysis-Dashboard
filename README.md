# Job Market Analysis Dashboard

This repository contains the Power BI files and associated documentation for the **Job Market Analysis Dashboard**. This interactive dashboard provides comprehensive insights into current job market trends, salary landscapes, regional job distribution, and detailed job posting analytics.

## Table of Contents
1.  [Project Description](#project-description)
2.  [Dashboard Purpose](#dashboard-purpose)
3.  [Dashboard Sections & Key Insights](#dashboard-sections--key-insights)
4.  [Data Model Schema](#data-model-schema)
5.  [Getting Started](#getting-started)
6.  [How to Use the Dashboard](#how-to-use-the-dashboard)
7.  [Contact](#contact)

## 1. Project Description

The Job Market Analysis Dashboard is a robust Power BI solution designed to offer a data-driven perspective on the dynamic job market. It consolidates diverse data points related to job postings, skills, salaries, and geographical distribution into an intuitive and interactive visual experience. This tool empowers stakeholders, including recruiters, HR professionals, strategic planners, and job seekers, to make informed decisions based on real-time market conditions.

## 2. Dashboard Purpose

The primary purpose of this dashboard is to:
* **Provide a Holistic Market View:** Offer an overall understanding of job posting volumes, popular job titles, and in-demand skills.
* **Analyze Salary Benchmarks:** Present insights into average, median, minimum, and maximum salaries across various job schedules, skills, companies, and specific job titles.
* **Identify Regional Trends:** Highlight the top countries for job opportunities and visualize job distribution globally.
* **Track Market Evolution:** Monitor month-over-month and year-over-year trends in job postings, skill demand, and preferred job schedule types.
* **Support Strategic Talent Acquisition:** Inform recruitment strategies by pinpointing critical skills, key hiring companies, and high-demand locations.
* **Aid Career Planning:** Offer valuable data for individuals and organizations to understand market demand for different roles and skill sets.

## 3. Dashboard Sections & Key Insights

The dashboard is organized into several key pages, each focusing on a different aspect of job market analysis:

* **Main Page:**
    * **Purpose:** Serves as a central navigation hub, providing quick access to all detailed analysis sections.
    * **Key Insights:** Offers an intuitive starting point for users to explore specific areas of interest.

* **Job Posting Analysis:**
    * **Purpose:** Provides a detailed breakdown of job postings by various dimensions.
    * **Key Insights:** Understand total job volumes, top job titles, skills requested for each job title, leading platforms, and top hiring companies. Analyze the prevalence of different job schedule types (e.g., full-time, contract, remote work trends like "Work from home").

* **Salary Insights:**
    * **Purpose:** Offers comprehensive analysis of salary data across different dimensions.
    * **Key Insights:** Benchmark salaries (average, median, min, max) by job schedule, specific skills, companies, and job titles. Identify high-paying skills and roles.

* **Regional Job Market Analysis:**
    * **Purpose:** Visualizes the geographical distribution of job postings and identifies top countries and their specific demands.
    * **Key Insights:** Pinpoint leading countries by job volume, analyze demand for specific job titles and skills within those countries, and understand regional preferences for job schedule types.

* **Job Market Trends:**
    * **Purpose:** Provides a time-series analysis of job market indicators to track evolution over time.
    * **Key Insights:** Monitor monthly job posting volumes, track the rise or fall in demand for specific skills, and observe shifts in the popularity of different job schedule types over time.

## 4. Data Model Schema

The dashboard is built upon a robust star schema data model designed for efficient querying and analysis in Power BI. Key tables and their relationships are as follows:

* **`job_post_fact` (Fact Table):**
    * The central table containing individual job posting records.
    * Includes measures like job counts (`job_posts`).
    * Related to dimension tables via foreign keys.

* **`Company_dim` (Dimension Table):**
    * Contains details about the companies posting jobs.
    * Linked to `job_post_fact` to filter and group by company.

* **`DateTimeTable` (Dimension Table):**
    * A standard date dimension table used for all temporal analysis (e.g., year, month, day).
    * Linked to `job_post_fact` to enable time-based filtering and trends.

* **`job_schedule_type` (Dimension Table):**
    * Contains details about different job schedule types (e.g., Full-time, Contract, Internship, Part-time, Temporary, Work from home).
    * Linked to `job_post_fact` to analyze jobs by schedule.

* **`Skill_dim` (Dimension Table):**
    * Contains a list of unique skills identified in job postings.
    * Used in conjunction with `Skill_job_dim` to link skills to job postings.

* **`Skill_job_dim` (Bridge Table / Factless Fact):**
    * A linking table that connects `job_post_fact` to `Skill_dim`, allowing a many-to-many relationship where one job can require multiple skills and one skill can be required by multiple jobs.

* **`Measures_table` (Calculated Measures):**
    * A collection of pre-defined measures to facilitate common calculations and comparisons, such as `Posts_variance`, `Prev_month_topskill`, `previous_month`, `Skill_variance`, `Top Skill`, `Top_Skill_count`, etc.

* **`Top10Countries`, `Top10Skills`, `Top10Platform` (Lookup/Helper Tables):**
    * These likely contain pre-calculated or filtered lists of the top entities for easier display and filtering in the dashboard, improving performance for common "top X" analyses.

The schema is optimized to allow for flexible slicing and dicing of job market data across various dimensions (time, company, location, skill, job title, schedule type).

## 5. How to Use the Dashboard

* **Navigation:** Use the tabs at the bottom of the Power BI report or the navigation buttons on the "Main Page" to switch between different analysis sections.
* **Filters/Slicers:** Utilize the filters and slicers on the right sidebar or directly on the report pages (e.g., year, month, job title, country, skill, company) to narrow down your analysis.
* **Interactivity:** Click on elements within charts (e.g., a bar in a bar chart, a slice in a pie chart) to cross-filter other visuals on the same page.
* **Drill Down/Up:** Some visuals might offer drill-down capabilities (right-click or hover for arrows) to explore data at a more granular level.

## 6. Contact

For questions, feedback, or collaborations, please open an issue in this repository.

---
