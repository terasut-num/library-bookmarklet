# Primo DOI Search Utility

The Primo DOI Search Utility is a lightweight JavaScript tool designed to streamline the academic research process. It automatically extracts a Digital Object Identifier (DOI) from a webpage and initiates a Primo search using that DOI. This automation is especially useful for researchers needing quick access to full-text articles through the Primo discovery system.

---

## Table of Contents

- [Introduction](#introduction)
- [Code Structure Overview](#code-structure-overview)
- [Component Details](#component-details)
  - [Constant](#constant)
  - [Functions](#functions)
    - [openPrimoSearch(doi)](#openprimosearchdoi)
    - [getDoiFromMeta()](#getdoifrommeta)
    - [getDoiFromSageMeta()](#getdoifromsagemeta)
    - [getDoiFromPageContent()](#getdoifrompagecontent)
- [Main Execution Flow](#main-execution-flow)
- [Bookmarklet Installation & Usage](#bookmarklet-installation--usage)
- [Conclusion](#conclusion)

---

## Introduction

The utility simplifies the process of accessing articles via Primo by:
- **Automatically extracting DOIs:** Detects DOI from meta tags or from the page content using regular expressions.
- **Constructing a Primo search URL:** Appends the extracted DOI to a base Primo URL.
- **Opening a new browser window:** Displays search results directly to the user.

This tool is optimized for both standard pages and SAGE-hosted pages, ensuring robust performance across multiple formats.

---

## Code Structure Overview

The project is structured into three main sections:

1. **Constants:**  
   - Contains global parameters like the Primo base URL.

2. **Functions:**  
   - Modular functions handle DOI extraction from various sources and manage the construction of the Primo search URL.

3. **Main Execution Logic:**  
   - Orchestrates the DOI extraction and search process by selecting the appropriate method based on the webpage context.

---

## Component Details

### Constant

#### `BASE_PRIMO_URL`
- **Purpose:**  
  Holds the base URL required for constructing the Primo search URL.
- **Usage:**  
  This constant is used as the foundation to which DOI-specific parameters are appended.

---

### Functions

#### openPrimoSearch(doi)
- **Purpose:**  
  Constructs the complete Primo search URL using the provided DOI and opens it in a new browser window.
- **Parameters:**  
  - `doi` (string): The Digital Object Identifier.
- **Behavior:**  
  - Appends the DOI to the `BASE_PRIMO_URL` using query parameters (`rft_id` and `rft.doi`).
  - Opens the URL in a new window and focuses on it.

---

#### getDoiFromMeta()
- **Purpose:**  
  Extracts the DOI from meta tags within the webpage.
- **Behavior:**  
  - Iterates through `<meta>` tags to find one with `name="citation_doi"`.
  - Returns the DOI from the `content` attribute if found.
- **Return Value:**  
  - The DOI as a string or `null` if not present.

---

#### getDoiFromSageMeta()
- **Purpose:**  
  Extracts the DOI from SAGE-hosted pages.
- **Behavior:**  
  - Searches for a `<meta>` tag with `property="dc.Identifier"`.
  - Converts the DOI by replacing underscores (`_`) with forward slashes (`/`).
- **Return Value:**  
  - The formatted DOI string or `null` if not found.

---

#### getDoiFromPageContent()
- **Purpose:**  
  Uses regular expressions to find DOI(s) in the entire HTML content of the page.
- **Behavior:**  
  - Scans the page for patterns that match typical DOI formats.
  - If a single DOI is found, it is returned immediately.
  - When multiple DOIs are detected, the function selects the most frequently occurring one. If frequencies are ambiguous, it returns `null`.
- **Return Value:**  
  - The selected DOI as a string, or `null` if none or ambiguous.

---

## Main Execution Flow

1. **DOI Extraction:**
   - The script first attempts to extract the DOI using `getDoiFromMeta()`.
   - If no DOI is found and the hostname is `journals.sagepub.com`, it uses `getDoiFromSageMeta()`. An alert notifies the user if no DOI is found on SAGE pages.
   - If still unresolved, it falls back to `getDoiFromPageContent()` to search for the DOI in the full HTML content.
   
2. **Initiating Primo Search:**
   - Once a valid DOI is extracted, `openPrimoSearch(doi)` is invoked to open the corresponding Primo search in a new window.
   - If no DOI is found after all attempts, the user receives an alert indicating the absence of a DOI on the website.

---

## Bookmarklet Installation & Usage

This JavaScript code can be used as a bookmarklet so that you can easily activate it while browsing any article webpage. Follow these steps to add and use the bookmarklet in your browser:

### Step 1: Use the Bookmarklet Code from the GitHub Repository

- **Access the Code:**  
  The bookmarklet code is available in my GitHub repository **[library-bookmarklet](https://github.com/yourusername/library-bookmarklet)** under the filename `primo_bookmarkletv1.js`.
  
- **Minification Requirement:**  
  For bookmarklet use, the code should be minified (all on one line without extra spaces or line breaks). You can either use the minified version provided in the repository or use an online minifier to process `primo_bookmarkletv1.js`.

### Step 2: Create a New Bookmark

1. **Open the Bookmarks Manager:**  
   In your browser, access the bookmarks manager or display the bookmark bar.
   
2. **Create a New Bookmark:**  
   - **Name:** Choose a descriptive name such as "Primo DOI Search".
   - **URL/Location:** Paste the entire minified bookmarklet code (starting with `javascript:`) into the URL field.
   - **Save:** Store the new bookmark.

### Step 3: Using the Bookmarklet

- **Navigate to an Article Page:**  
  When you are on a webpage with an article (or any page that might contain a DOI), simply click the "Primo DOI Search" bookmark.
  
- **Automatic Execution:**  
  The bookmarklet will execute the script, attempt to extract the DOI, and if successful, open a new window with the Primo search results.
  
- **Alerts:**  
  If the script cannot find a DOI, an alert will notify you that no DOI was found on the current page.

This approach allows you to integrate the Primo DOI search functionality directly into your regular browsing experience, saving time and streamlining your research workflow.

---

## Conclusion

The Primo DOI Search Utility automates the task of DOI extraction and Primo search initiation, making it an invaluable tool for researchers. Its multi-method approach ensures high reliability, and its modular design supports easy maintenance and future enhancements. By converting the script into a bookmarklet and hosting it in the **library-bookmarklet** repository, users can quickly trigger a search from any article webpage with minimal effort.

---

---

# Project II: EZproxy-bookmarklet
## How to use this bookmarklet?

**Step 1: Setup this bookmarklet (Javascript)**

	• 1) Add a new bookmark in your browser
	
	• 2) Set the name or title to a memorable phrase Ex: MU
	
	• 3) The URL must be configured to use one of these two codes from Mahidol-bookmarklet.js [Figure 1]
  

<img src="https://user-images.githubusercontent.com/118581170/219703046-957c45bc-a69d-444d-b623-67c707f836df.png" width="720">

🖼️ Figure 1: Setup the EZproxy link generator (bookmarklet)

&nbsp;
&nbsp;

**Step 2: Using the bookmarklet [Figure 2]**

	• To access the Mahidol E-database from the page you are on, simply click this bookmark.
 
<img src="https://user-images.githubusercontent.com/118581170/219703107-26af6901-8a7f-4b25-afa0-d796b942f6fd.png" width="720">

🖼️ Figure 2: Using the EZproxy link generator (bookmarklet)


