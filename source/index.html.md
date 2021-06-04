---
title: Jido Map API - DWG File Specification



toc_footers:
  - <a href='https://www.jidomaps.com'>Jido Maps Inc.</a>


search: true

code_clipboard: false
---

# Introduction

The Jido Map API will offer a comprehensive API end-point to receive: 
 
 - Map layouts of the store
 - Product location data
 - Point of interest location data
 - Dynamic navigation routes
 - Turn-by-turn navigation instructions

The Jido Map API is designed to work with the current AutoCAD (DWG) layout files that are produced for each IKEA store. In order to ensure that key data is up-to-date and accurate, some additional layers are created in this DWG file that follow the clear guidelines outlined in this document. To ensure customer guidance looks and behaves in the best possible way for customers, it is important to follow these guidelines as well as keeping the DWG file in sync with Jido in the event the store layout changes.

Should you have any questions or suggestions regarding the guidelines in this document or the Jido Map API, please reach out to Support-IKEA@jidomaps.com.


# Overview

A well-formed DWG file will contain 9 additional jido specific layers, each named with a "jido-" prefix. These layers utilize AutoCad poly-lines and text elements to precisely describe:
 
 - The main walking path in the Showroom and Market Hall
 - Shortcuts in the Showroom and Market Hall
 - The outline of the main structural walls in store that guide and restrict commercial traffic
 - The location of walls that divide between store sections
 - The position of all the ceiling grid locations in the store
 - The locations of commercial areas (HFB sections, PA areas)
 - Key points of interest in the store including: "restroom", "elevators", "stairs", "cafeteria", etc.

# Jido Layers

Each of these additional layers can be created by simply tracing the correct data already contained in the DWG file. Since each store likes to manage their DWG files slightly differently, it is important to consider the end result that each layer is meant for.

Please ensure the layer uses the exact titles listed below.

## Layer: Walls

**Purpose:** Define the walls to be shown on the customer facing map
**Title:** jido-walls
**Specification:** Using poly-lines, trace all the walls and permanent barriers that guide and restrict the movement of foot-traffic in the store. 

Lines should be placed as close to the center of wall as possible. 


> <pre style="background-color: initial; padding: 0">
> <a href="https://lh3.googleusercontent.com/2EZ02VV76JQp--aEfiLYpJkT0slAFucRd1m9qp6wOn5IBDbkQ7xm8aqQrPLA74UGM4u2hn5_g8jlhWTIMCHvcA9FX27aWg-ZFVgymvUa_WgAjHUphdA5xBKI_n460JQYgZq7WFUZ">
> <img src="https://lh3.googleusercontent.com/2EZ02VV76JQp--aEfiLYpJkT0slAFucRd1m9qp6wOn5IBDbkQ7xm8aqQrPLA74UGM4u2hn5_g8jlhWTIMCHvcA9FX27aWg-ZFVgymvUa_WgAjHUphdA5xBKI_n460JQYgZq7WFUZ">
> </a>
> </pre>


### Notes:

 - **Walls can be simplified as long as the simplification does not hide an important path which customers may need to take. For example, small gaps in walls can be removed and instead shown as contiguous walls.**
 - Walls that are not in or adjacent to a space with customer foot-traffic do not need to be traced. Sections of the store where customers do not go will not be shown on the map.
 - Walls with a door through which customers can pass should be indicated by an opening in the wall and a break in the wall-line corresponding to the width of said door.



## Layer: Walking Path

**Purpose:** Define the main walking path that guides customer traffic in the store
**Title:** jido-walking-path
**Specification:** Using poly-lines, trace the main walking path that guides foot-traffic in the store.

Lines should be placed as close to the center of the walking path as possible.

Additionally, the start and end points of the walking path should be labeled. An AutoCAD single-line text element should be placed at the start of the walking path and at the end of the walking path. The start-block should have the text value "path-start" and the end-block should have the label-attribute value "path-end." (This is important for automatically determining and extracting the directionality of the walking path from the map file.)


> <pre style="background-color: initial; padding: 0">
> <a href="https://lh5.googleusercontent.com/ni0WV9rqLkLYYNC1u1QXH0gKT6-zbHqEj8EZMs9bYq81TSHtvSEfLWh5dVE05hMQ4GT5ZIadvPw_QOCrDW3QvsFIOK4Wozr9pbz381W8AEmU__c8BOItexQsfE6HPUs6IkM0MV-d">
> <img src="https://lh5.googleusercontent.com/ni0WV9rqLkLYYNC1u1QXH0gKT6-zbHqEj8EZMs9bYq81TSHtvSEfLWh5dVE05hMQ4GT5ZIadvPw_QOCrDW3QvsFIOK4Wozr9pbz381W8AEmU__c8BOItexQsfE6HPUs6IkM0MV-d">
> </a>
> </pre>


## Layer: Shortcuts

**Purpose:** Define the shortcuts that connect different parts of the store that are not directly connected by the walking path.
**Title:** jido-shortcuts
**Specification:** Using a set of lines, make connections between different points on the walking path that are accessible by a shortcut



> <pre style="background-color: initial; padding: 0">
> <a href="https://lh4.googleusercontent.com/D48S-jaFgyBfrILVCJZdigBU6Oo-gqbGxlo8xBTWFyQhcHofg5EVmsVkcocg12TixUNJLWPiXrUNI3KorK_pW9SYnPsb0b3M-YoRBSXuk9dsm0SaCwbiqTXjIOkG8DIDVh-4Q8TF">
> <img src="https://lh4.googleusercontent.com/D48S-jaFgyBfrILVCJZdigBU6Oo-gqbGxlo8xBTWFyQhcHofg5EVmsVkcocg12TixUNJLWPiXrUNI3KorK_pW9SYnPsb0b3M-YoRBSXuk9dsm0SaCwbiqTXjIOkG8DIDVh-4Q8TF">
> </a>
> </pre>


## Layer: Product Displays

**Purpose:** Define the area in the store occupied by room sets, room set walls and other product display areas that impede walking traffic in the store. 
**Title:** jido-product-displays
**Specification:** Use rectangular or polygonal areas to identify the different room set areas or other product display areas. 

**Note:** These regions will be used for determining efficient and unimpeded paths throughout the store and do not need to be labeled.


> <pre style="background-color: initial; padding: 0">
> <a href="https://lh5.googleusercontent.com/oZq9KhPiwqZ05tzbS-O0B97glGYpegdNXZvPO-Pl_kdfFXubAzhJCyVoBHYZ_ibs37GxCihnNvAaAWu7dR9Coaq0b4_kNM7WUErnOr5HC9ynvNv4ISIsIqTRSHXh-QUmhME1pos-">
> <img src="https://lh5.googleusercontent.com/oZq9KhPiwqZ05tzbS-O0B97glGYpegdNXZvPO-Pl_kdfFXubAzhJCyVoBHYZ_ibs37GxCihnNvAaAWu7dR9Coaq0b4_kNM7WUErnOr5HC9ynvNv4ISIsIqTRSHXh-QUmhME1pos-">
> </a>
> </pre>


## Layer: Navigation Points

**Purpose:** Define the set of points in the store that are destinations that a user can navigate to.
**Title:** jido-navigation-points
**Specification:** A set of single-line text elements with unique text values should be used to label all the possible "navigation points", or destinations that a customer can navigate to in the store. Where applicable, navigation points should include at least: "restroom", "cafeteria", "elevator", "checkout", and "stairs".
**Note:** The size or style of the text element does not matter, but the geometry position values of the text element should be placed directly on top of the point on the map that corresponds to that label.


> <pre style="background-color: initial; padding: 0">
> <a href="https://lh3.googleusercontent.com/0K_y787hYlwl_-k8O4dcfnoYXz2x3zfz-SMpIIm7JteFISGGTGQs3O0ErJJajLXdAYio6TV_zFCo1JsA1sgUWDhJw_cqHjQ5Y0x4cFd-Eq-vVGO_KbOdFoRf818iBVPRNgZmf6JX">
> <img src="https://lh3.googleusercontent.com/0K_y787hYlwl_-k8O4dcfnoYXz2x3zfz-SMpIIm7JteFISGGTGQs3O0ErJJajLXdAYio6TV_zFCo1JsA1sgUWDhJw_cqHjQ5Y0x4cFd-Eq-vVGO_KbOdFoRf818iBVPRNgZmf6JX">
> </a>
> </pre>

## Layer: Ceiling Grid Locations

**Purpose:** Define the set of points that correspond to ceiling-grid-locations on the map.
**Title:** jido-grid-locations
**Specification:** A set of single-line text elements with unique text values that correspond to a unique grid location on the map.
**Note:** The size or style of the text element does not matter, but the geometry position values of the text element should be placed directly on top of the point on the map that corresponds to that label.


## Layer: PA Locations

**Purpose:** Define the set of points that correspond to PA locations on the map.
**Title:** jido-PA-locations
**Specification:** A set of single-line text elements with unique text values that correspond to a PA locations on the map. Optionally, PA regions can be represented by non-overlapping rectangles or polygonal regions corresponding to the area of that PA region.
**Note:** The size or style of the text element does not matter, but the geometry position values of the text element should be placed directly on top of the point on the map that corresponds to that label.

## Layer: HFB Locations

**Purpose:** Define the set of points that correspond to HFB locations on the map.
**Title:** jido-HFB-locations
**Specification:** A set of single-line text elements with unique text values that correspond to a HFB locations on the map. Optionally, HFB regions can be represented by non-overlapping rectangles or polygonal regions corresponding to the area of that HFB region.
**Note:** The size or style of the text element does not matter, but the geometry position values of the text element should be placed directly on top of the point on the map that corresponds to that label.


## Layer: Map Features (optional)

**Purpose:** Define the set of points or regions on the map that may be displayed in a view of the map generated for users.
**Title:** jido-map-features
**Specification:** Map features may include the rectangular region occupied by the elevators or the stairs in the store, roomsets, signage, etc. There are no restrictions on the shape or name of a map-features. The map-features layer can contain any number of labels of any shape or type including poly-lines and rectangular regions. 

The jido-map layers to include in the dwg file for extraction and parsing by our backend:


> <pre style="background-color: initial; padding: 0">
> <a href="https://lh4.googleusercontent.com/iXp1dJ7VtrwszHr97AgKzLJOOvWbW53qY_yrM3Xk6ePYFchIvh0tHBnm7LN4jziM7rgpBqRqf1qdDbhzgnWaaiPYtL7Iy1ZFisLc1Zuob_fFCDAcA_iVp4eIK469DQfSsqpHHFH-">
> <img src="https://lh4.googleusercontent.com/iXp1dJ7VtrwszHr97AgKzLJOOvWbW53qY_yrM3Xk6ePYFchIvh0tHBnm7LN4jziM7rgpBqRqf1qdDbhzgnWaaiPYtL7Iy1ZFisLc1Zuob_fFCDAcA_iVp4eIK469DQfSsqpHHFH-">
> </a>
> </pre>


An IKEA dwg map with some additional annotations including:

 1. "path-start" label (jido-walking-path layer)
 2. "restroom" label (jido-navigation-points layer)
 3. Lines for wall positions (jido-walls layer)
 4. Lines for the walking path (jido-walking-path layer)



> <pre style="background-color: initial; padding: 0">
> <a href="https://lh3.googleusercontent.com/RCeF77REiDkPXYsDBQE9rxF_JBf0U9lB1d17lojJuAGJZWMrEXUQE2A73ABTf18nEBiJ4WqKMbMHAKOBgxqNCb52NNMbxDfp3SeSLF3U5OyVMMZD0wJ_bR_7n_7Wkn5fxsrYK95A">
> <img src="https://lh3.googleusercontent.com/RCeF77REiDkPXYsDBQE9rxF_JBf0U9lB1d17lojJuAGJZWMrEXUQE2A73ABTf18nEBiJ4WqKMbMHAKOBgxqNCb52NNMbxDfp3SeSLF3U5OyVMMZD0wJ_bR_7n_7Wkn5fxsrYK95A">
> </a>
> </pre>



> <pre style="background-color: initial; padding: 0">
> <a href="https://lh5.googleusercontent.com/QB1bmNeWY0nQijI1Xk0LxFN6mACSv1T4-0TLWwZR0GmrcoUkQGjU0ykQWbIfVb6165vLsTgcGyxOuJRxlO_nnZAQZDr4LWTajdp341kciQp3dS2XUmjFOkTh5RyeRuW7LRYJtUSE">
> <img src="https://lh5.googleusercontent.com/QB1bmNeWY0nQijI1Xk0LxFN6mACSv1T4-0TLWwZR0GmrcoUkQGjU0ykQWbIfVb6165vLsTgcGyxOuJRxlO_nnZAQZDr4LWTajdp341kciQp3dS2XUmjFOkTh5RyeRuW7LRYJtUSE">
> </a>
> </pre>