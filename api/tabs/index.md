---
title: "Tabs"
parent: API Documentation
has_children: true
layout: default
nav_order: 2
permalink: /api/tabs/
---

# Tabs Overview

A **Tab** represents a container for multiple **Columns** (panels) and serves as a structured interface element to organize items, options, or functionalities. All tabs derive from `BaseTab`, which provides core functionality and standard properties.

### Core Features

- **Columns**: Each tab contains up to four main columns:
  - **LeftPanel**
  - **CenterPanel**
  - **RightPanel**
  - **BottomPanel**
  
  Columns handle item display, selection, navigation, and interaction within the tab.

- **BottomPanel**: A description panel that displays information about the currently selected item. It can only be shown or hidden, and its content is automatically updated based on item selection. It **cannot be replaced** with another type of panel.
- **IBPanel**: All Tabs include an instructional buttons panel (`IBPanel`) to show context-sensitive instructions or hints while navigating.

- **Context Menu**: Each tab have a **ContextColumn**, a contextual menu displayed above the currently selected item. Context items (`ContextItem`) can be simple actions (e.g., "Use", "Throw") or selectable items with quantities (e.g., "Give", "Take").

- **Navigation & Selection**: Tabs support keyboard/gamepad-style navigation through columns and items, including methods like `GoUp`, `GoDown`, `GoLeft`, `GoRight`, `Select`, and `GoBack`.

- **Events & Callbacks**: Tabs provide hooks such as `Activated` to handle when a tab is selected or becomes active.

### Summary

Tabs offer a flexible way to structure content, combining multiple panels, context menus, selectable items, and instructional hints. They act as the foundation for most interactive UI features in the system, ensuring consistency and modularity with support for separate inventories co-existing into the same macro inventory.