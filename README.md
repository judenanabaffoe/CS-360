Warehouse Inventory App — CS 360 Portfolio Artifact
Project Summary & User Goals
The Warehouse Inventory App is an Android-based inventory management application engineered to solve critical tracking bottlenecks for small-to-medium enterprises (SMEs) and warehouse floor operations. The primary objective is to replace error-prone, static tracking methods with a reliable, offline-first digital database. The application addresses key user needs by enabling floor staff to execute instant Create, Read, Update, and Delete (CRUD) operations on stock levels and configure automated low-stock SMS alerts to prevent supply chain disruptions and costly stock-outs.

User-Centered UI & Feature Architecture
To support efficient warehouse workflows, the app is organized into four core screens designed around high scannability and minimal tap friction:

Login Screen (LoginActivity): Provides a clean, focused entry point for secure user authentication while isolating database access from unauthorized users.

Inventory Dashboard (InventoryActivity): Features a structured RecyclerView displaying item names, SKU placeholders, quantities, and direct row-level delete actions. An Extended Floating Action Button (FAB) provides immediate access to item creation without cluttering the screen.

Add Item Screen (AddItemActivity): Implements a direct data-entry form with strict input validation to sanitize user data before committing changes to the database.

SMS Permission & Alerts Screen (SmsPermissionActivity): Utilizes contextual messaging to explain why telephony access is required before triggering runtime prompts, complete with dynamic visual state banners indicating whether permissions are granted or denied.

The UI leverages a high-contrast industrial theme (dark steel, safety amber accents, and clean white data cards) to ensure optimal readability on warehouse floor devices.

Coding Strategies & Engineering Approach
The application follows modern Android software architecture and modular programming principles:

Separation of Concerns: Database management is encapsulated within a dedicated DatabaseHelper class extending SQLiteOpenHelper, decoupling raw SQL operations from UI controllers.

Dynamic Data Binding: A custom InventoryAdapter acts as the bridge between raw SQLite database cursors and the RecyclerView, managing view recycling for memory efficiency and smooth scrolling.

Defensive Programming: Numerical inputs are safely handled with try-catch blocks catching NumberFormatException to prevent crashes from invalid character entry.

Graceful Degradation: The permission architecture checks system capabilities via ContextCompat.checkSelfPermission() and allows full local database functionality even if the user denies SMS access.

These strategies establish reusable architectural patterns for future projects requiring robust local persistence, clean data decoupling, and strict permission compliance.

Testing & Quality Assurance
The codebase was verified through systematic manual and runtime testing using Android Studio’s emulator suite and debugging tools:

Runtime Diagnostics: Android Studio's Logcat was utilized extensively to monitor activity lifecycle transitions and catch runtime exceptions.

Edge-Case Validation: Form inputs were tested against empty strings, non-numeric quantity values, and rapid repeated submissions to verify input validation safeguards.

State Persistence & CRUD Verification: Tested database persistence by creating items, verifying immediate UI updates, triggering row deletions, and confirming data integrity across activity rebuilds (onResume()) and cold app restarts.

Permission Testing: Verified both "Allow" and "Deny" paths for runtime SMS permissions to ensure proper visual feedback toggles without crashing the application.

Overcoming Challenges & Innovation
A key challenge during development was ensuring instant visual synchronization between SQLite database mutations and the user interface. Rather than incurring the overhead of completely re-instantiating activities upon data modification, I implemented a dynamic swapCursor() routine within the InventoryAdapter. This method safely closes existing database cursors, binds the updated query results, and notifies the adapter via notifyDataSetChanged(), providing instant UI updates with optimal memory management.

Demonstrated Technical Expertise
This project successfully demonstrates advanced competency in native Android lifecycle management, SQLite persistence architecture, and hardware-level permission handling. By bridging low-level SQL database transactions with a modern, responsive Material Design interface, the completed artifact reflects end-to-end mobile development capabilities—from requirement analysis and UI wireframing to secure implementation and Google Play deployment readiness.
