# AL Development Guidelines

## 🔤 Naming Conventions
- Use **PascalCase** for all object names (Tables, Pages, Codeunits, Enums, etc.)
- Use **camelCase** for variable and function names.
- Events: `On[Action]` (e.g., `OnBeforeInsert`)
- File names for extensions should match the standard object name with a prefix (e.g., `CITSalesOrder.TableExt.al` for a Sales Order table extension).

## 🧱 Code Structure
- Use **regions** (`#region`, `#endregion`) to organize codeunits
- Group methods by functionality (e.g., Public API, Internal Logic, Event Publishers)
- Follow the same structure and namespaces as used in the Microsoft standard base application.

## 🧰 Commonly Used Methods and Patterns
- **Recursion for data processing**: Use recursive functions to handle hierarchical data structures like BOMs or account trees.
- **Temporary Tables for performance**: Use temporary records to reduce database I/O and improve performance in batch operations.
- **SetLoadFields for performance optimization**: Use `SetLoadFields` to load only required fields from the database, improving performance.
- **FilterGroup for advanced filtering**: Use `FilterGroup` to apply multiple independent filters on a record for complex queries.

## AL internal Coding Conventions for Business Central Development
Always use this conventions for AL Code:
- Variable names **must not** contain any prefix unless a naming conflict arises.
- Variable names **must always** include the AL object name they belong to.
- Variable names **must not** contain any special characters.
- **Always** define a `Caption` for table fields, even if the field name is identical to the caption.
- If a caption is intentionally left empty, the `Locked` property **must** be set to `true`.
- Omit the `DataClassification` property
- The name of the event subscriber **must** be identical to the name of the event it subscribes to.
- Only the parameters that are **actually used** in the subscriber should be passed.
- Event subscribers **must always** be placed in a `Codeunit` that has the **same name** as the object to which the event belongs.
- Do **not** use `addbefore`, `addafter`, `movebefore`, or `moveafter` in `PageExtension` objects.
- Use call by reference (`var`) **only** if the variable is modified within the procedure.