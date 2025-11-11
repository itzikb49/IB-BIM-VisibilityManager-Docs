# Frequently Asked Questions (FAQ)

## 📑 Table of Contents

1. [General Questions](#general-questions)
   - Revit version support
   - Cross-project compatibility
   - Template support

2. [Workflow & Operations](#workflow--operations)
   - How COPY works
   - How REMOVE works
   - Template detection & warnings
   - Views vs Templates selection
   - Applying to single template-based view

3. [Filters](#filters)
   - Template handling
   - Name conflicts (Merge/Overwrite/New Only)
   - Custom parameters
   - Supported rule types

4. [VG Overrides](#vg-overrides)
   - Difference from Filters
   - Use cases
   - Export both Filters and VG

5. [Export/Import](#exportimport)
   - How Export works (source view)
   - How Import works (target view)
   - Import to multiple views
   - Export from Templates vs Views
   - PAT file purpose
   - Excel vs CSV

6. [Performance](#performance)
   - Capacity limits
   - Speed

7. [Troubleshooting](#troubleshooting)
   - Filters don't appear
   - "Value" instead of actual values
   - Pattern not found warnings
   - Custom parameters not created

8. [Licensing & Support](#licensing--support)
   - License per version
   - Multi-user licensing
   - Support channels
   - Bug reporting

9. [Tips & Best Practices](#tips--best-practices)
   - Filter organization
   - Coordination meetings
   - Template workflows

---


## General Questions

### Q: What Revit versions are supported?
**A:** Visibility Manager supports Revit 2023, 2024, 2025, and 2026. Each version has a dedicated optimized build.

### Q: Does it work with templates?
**A:** Yes! The tool intelligently detects if a view uses a template and reads filter settings from the template automatically. When copying filters, you can choose to apply to views directly or to their templates.

### Q: Can I use this across different projects?
**A:** Absolutely! Export filters from one project and import them into any other project. The tool handles missing parameters and patterns automatically.

---

## Workflow & Operations

### Q: How does the COPY function work?
**A:** COPY duplicates selected filters or VG overrides from your current view to target views/templates.

**Key points:**
- **Current view = Source (reference only)** - Shows what to copy but is NOT modified
- **Columns 2-3 = Targets** - Where filters/overrides are copied TO
- Works identically for both Filters and VG Overrides

**Step by step:**
1. Open a view that has the filters/overrides you want to copy (source)
2. **Left panel**: Select which filters or overrides to copy
3. **Column 2**: Select target views
4. **Column 3**: Select target templates (optional)
5. Click **COPY**
6. Choose conflict resolution if items already exist:
   - **Merge** - Keep existing, add new ones
   - **Overwrite** - Replace existing with imported settings
   - **New Only** - Skip existing, add only new ones

**Example:**
- Current view has 15 filters
- Select 8 filters
- Select 20 target floor plan views
- Click COPY
- Result: Those 8 filters now exist in all 20 views
- Current view unchanged (still has original 15 filters)

**Note:** Current view is never modified - it's your reference!

---

### Q: How does the REMOVE function work?
**A:** REMOVE deletes selected filters or VG overrides from target views/templates.

**Key points:**
- **Current view = Reference only** - Shows what to remove but is NOT modified
- **Columns 2-3 = Targets** - Where filters/overrides are removed FROM
- Works identically for both Filters and VG Overrides

**Step by step:**
1. Open any view (used as reference)
2. **Left panel**: Select which filters or overrides to remove
3. **Column 2**: Select views to remove from
4. **Column 3**: Select templates to remove from (optional)
5. Click **REMOVE**
6. Confirmation dialog appears
7. Selected items are removed from all target views/templates

**Example:**
- Current view shows 10 filters
- Select 3 outdated filters
- Select 15 target views
- Click REMOVE
- Result: Those 3 filters are removed from all 15 views
- Current view unchanged (still has all 10 filters)

**Use case:** Clean up multiple views by removing outdated or incorrect filters/overrides at once.

---

### Q: What happens when target views use templates?
**A:** The tool **detects templates automatically** and shows a warning:

**Warning dialog:**
```
⚠️ Template Detected

The following views use templates. 
Applying changes will affect ALL views using these templates:

- Template: "Architectural Floor Plan" (used by 15 views)
- Template: "MEP Coordination" (used by 8 views)

Total views that will be affected: 23

Do you want to continue?
[Yes] [No]
```

**What this means:**
- When you select a view that uses a template (Column 2)
- The tool applies changes to the **template itself**
- This affects **ALL views** using that template
- This is **Revit's behavior**, not a tool limitation

**Why?**
- In Revit, when a view uses a template, filter/VG settings are controlled by the template
- You cannot modify a view independently without breaking the template link
- The tool follows Revit's rules correctly

**Your options:**
1. **Continue [Yes]** - Apply to templates (standard workflow)
   - All views using those templates will be updated
   - Usually the desired behavior for coordination!
   
2. **Cancel [No]** - Stop and reconsider
   - Review which views are selected
   - Decide if you want to affect that many views
   
3. **Work with templates directly** - Select from Column 3 instead
   - More explicit about what you're doing
   - Same result, clearer intent

**Best practice:**
- Review the warning carefully
- Understand how many views will be affected
- This is usually what you want for standardization!
- For one-off views, remove template in Revit first

---

### Q: Should I select Views (Column 2) or Templates (Column 3)?
**A:** Both columns work, but there are strategic differences:

**Column 2 - Target Views:**
- Select views by name (Floor Plan: Level 1, Level 2, etc.)
- ⚠️ **If view uses template** → Tool applies to the template (warns you first)
- ✓ **If view has NO template** → Applies only to that view
- **Use when:** You want to select specific views by their names

**Column 3 - Target Templates:**
- Select templates directly (Architectural Plan, MEP Coordination, etc.)
- ✓ Always applies to template
- ✓ Affects ALL views using that template
- ✓ More efficient for bulk standardization
- ✓ Clearer intent - you know you're modifying a template
- **Use when:** You want to standardize multiple views using the same template

**Example workflows:**

**Scenario 1: Standardize all architectural views**
- ✅ **Best approach:** Select template from Column 3
  - Pick "Architectural Floor Plan" template
  - All 20 views using it update instantly
  - Clear and explicit

**Scenario 2: Update specific views without templates**
- ✅ **Best approach:** Select views from Column 2
  - Pick individual views: "Level 1 - Working", "Level 2 - Working"
  - Only those views affected
  - No template complications

**Scenario 3: Mixed - some views with templates, some without**
- ⚠️ **Careful approach:** Select from Column 2
  - Tool warns about template-linked views
  - Review warning carefully
  - Proceed if acceptable
- 💡 **Alternative:** Two passes
  - First pass: Select templates from Column 3
  - Second pass: Select template-free views from Column 2

**Pro tip for coordinators:**
- Work with templates (Column 3) for discipline-wide standards
- Each discipline has its own template
- Update template → all coordination views update
- Ensures consistency across the team

---

### Q: Can I apply to both Views and Templates simultaneously?
**A:** Yes! You can select from both columns at once:
- Select specific views from Column 2
- AND select templates from Column 3
- Click COPY or REMOVE
- Tool processes all selections

**This is useful when:**
- You have some template-based views AND some standalone views
- You want to update everything in one operation
- Just be aware of the template warning if applicable

---

### Q: How can I apply to ONE view that uses a template without affecting others?
**A:** You need to break the template link first:

**In Revit (before using the tool):**
1. Open the view
2. Properties panel → View Template → `<None>`
3. View is now independent
4. Now use Visibility Manager - only this view will be affected
5. (Optional) Apply a different template afterwards if needed

**Why this is necessary:**
- Revit's architecture doesn't allow view-specific filter overrides when using templates
- This is a Revit limitation, not a tool limitation
- The tool correctly follows Revit's rules

**Alternative approach:**
- Accept that the template (and all views using it) will change
- Often this is actually the desired behavior for coordination!
- Templates exist specifically to keep multiple views synchronized

---

## Filters

### Q: What happens when the target view has a View Template?
**A:** This is covered in the **Workflow & Operations** section above.

The tool shows clear warnings and lets you choose the best approach.

### Q: What if filters with the same name already exist?
**A:** You have three options:
- **Merge** - Keeps existing filters, adds new ones
- **Overwrite** - Updates existing filters with imported settings
- **New Only** - Skips existing filters, imports only new ones

### Q: Can the tool handle custom parameters?
**A:** Yes! The tool:
- ✓ Automatically detects filters using custom parameters
- ✓ Exports full parameter definitions (name, type, category)
- ✓ Shows a dialog during import asking if you want to create missing parameters
- ✓ Creates parameters with correct settings automatically

### Q: What filter rules are supported?
**A:** All standard Revit filter rules:
- String: Contains, NotContains, Equals, NotEquals, BeginsWith, EndsWith
- Numeric: Equals, NotEquals, GreaterThan, LessThan, GreaterOrEqual, LessOrEqual
- Boolean: HasValue, HasNoValue
- Complex: AND/OR combinations, nested logic

---


## VG Overrides

### Q: What's the difference between Filters and VG Overrides?
**A:**

**Filters:**
- **Rule-based** - Show/hide elements matching conditions
- Example: "All Walls where Type Name contains 'GY'"
- Can be complex: AND/OR logic, multiple conditions
- Selective visibility

**VG Overrides:**
- **Category-based** - Graphics for ALL elements of a category
- Example: "All Walls" (every wall in the project)
- No conditions - affects entire category
- Graphic appearance only (colors, patterns, line weights)

**Both managed by this tool:**
- Same COPY/REMOVE workflow
- Same template detection
- Same three-column interface
- Same Export/Import process

### Q: Why use VG Override export/import?
**A:** To quickly standardize:
- **Line weights** - Consistent across views (walls: weight 3, doors: weight 1)
- **Colors** - Discipline-specific (structural: blue, MEP: red)
- **Fill patterns** - Presentations and sections
- **Halftone settings** - Background elements in coordination views

**Use case for coordinators:**
- Export VG from "master coordination view"
- Import to all team members' coordination views
- Everyone sees the same colors and line weights
- Eliminates "it looks different on my screen" issues

**Much faster than:**
- Manual Visibility/Graphics dialog work (20+ categories × 10+ views)
- Typing in line weights and selecting patterns repeatedly
- Trying to remember which category gets which color

### Q: Can I export both Filters and VG Overrides together?
**A:** No, they are separate operations by design:

**Why separate?**
- Different purposes (visibility rules vs. graphics)
- Different file structures
- Often used independently

**Workflow if you need both:**
1. Export Filters → Creates "ProjectName_Filters.xlsx"
2. Export VG Overrides → Creates "ProjectName_VG.xlsx"
3. Keep both files together
4. Import each separately to target project

**Best practice:**
- Maintain separate libraries for Filters vs. VG
- Filters: Organized by discipline and purpose
- VG: Organized by view type (coordination, presentation, construction)



## Export/Import

### Q: How does Export work - which view is used?
**A:** Export uses the **current active view** as the source:

**What gets exported:**
- All filters OR all VG overrides visible in the current view
- You can select which ones to export (left panel)
- Export creates Excel/CSV file + PAT file (for patterns)

**Important:**
- **Current view = Source (not modified)**
- Only what's in this view can be exported
- If you want to export filters from multiple views, export each view separately

**Example:**
1. Open view "Level 1 - Architectural"
2. This view has 20 filters
3. Select 15 filters to export
4. Export creates file with those 15 filters
5. Current view unchanged

**Best practice:**
- Create a "master" view with all standard filters
- Use this view for export to create your library
- This becomes your office standard

---

### Q: How does Import work - which view is affected?
**A:** Import applies to the **current active view**:

**What happens:**
- Filters/VG overrides are imported INTO the current view
- **⚠️ If current view uses a template:**
  - Tool detects this automatically
  - Shows warning: "This view uses template 'X' (Y views affected)"
  - Imports to the **template**, affecting ALL views using it
  - This is Revit's behavior
- **✓ If current view has NO template:**
  - Imports only to this specific view
  - No other views affected

**Step by step:**
1. Open the view where you want to import (target)
2. Click Import
3. Select Excel/CSV file
4. **If view uses template** → Warning appears
```
   ⚠️ Template Detected
   
   Current view uses template: "Architectural Floor Plan"
   This template is used by 15 views.
   
   Importing will affect ALL 15 views.
   
   Continue? [Yes] [No]
```
5. Review warning and decide
6. Filters/overrides are imported

**Important difference from COPY:**
- **COPY**: You select multiple target views (Columns 2-3)
- **IMPORT**: Only current view is the target
- **COPY**: Current view is reference (not changed)
- **IMPORT**: Current view IS changed

**Example scenarios:**

**Scenario 1: Import to single view**
- Open "Level 1 - Working" (no template)
- Import filters
- Result: Only this view updated ✓

**Scenario 2: Import to template-based view**
- Open "Level 1 - Architectural" (uses "Arch Template")
- Import filters
- Warning: "15 views use this template"
- Click Yes
- Result: Template updated, all 15 views updated ✓

**Scenario 3: Import to multiple views (workaround)**
- Can't do directly with Import
- Instead: Use this workflow:
  1. Import to ONE view first
  2. Then use COPY to distribute to other views
- OR: Import to each view separately

---

### Q: Can I import to multiple views at once?
**A:** Not directly with Import. Here's the recommended workflow:

**Method 1: Import → Copy**
1. Import filters to one view (gets them into the project)
2. Use COPY function to distribute to multiple views
3. This gives you more control over targets

**Method 2: Import to Template**
1. Open a view that uses the target template
2. Import (applies to template)
3. All views using that template update automatically
4. Most efficient for standardization!

**Method 3: Import repeatedly**
1. Open first target view → Import
2. Open second target view → Import
3. Repeat for each view
4. Less efficient but works

**Best practice for offices:**
- Create master views/templates with standard filters
- Export these to create a library
- New projects: Import to project template
- All views based on that template get the filters
- Maintains consistency across projects

---

### Q: Export from Template vs. Export from View - what's the difference?
**A:** There's NO difference - Export always uses what's visible:

**Key concept:**
- Export captures filters/VG from the current view's **display**
- If view uses a template, you see the template's filters → those get exported
- If view has no template, you see view-specific items → those get exported
- Export doesn't care about the source, only what's visible

**Example:**
- View "Level 1" uses template "Arch Template"
- Template has 20 filters
- Open "Level 1" and Export
- You export those 20 filters (from the template)
- Opening ANY other view using "Arch Template" would export the same 20 filters

**To export template filters:**
- Open ANY view using that template
- Export
- You get the template's filters

**To export view-specific items:**
- Open a view without a template
- OR remove a view from its template first
- Export
- You get view-specific items

**Pro tip:**
- No need to open templates directly
- Just open any view using the template
- Export from there - same result!


### Q: Why does the tool export a .PAT file along with Excel?
**A:** Revit fill patterns are stored separately from filters. The .PAT file contains:
- All fill patterns used in your filters
- Pattern definitions (lines, angles, spacing)
- Both drafting and model patterns

This ensures that when you import filters to another project, all patterns are available and filters display correctly. Without the .PAT file, filters would import but show missing pattern warnings.

### Q: What if the .PAT file is missing during import?
**A:** The tool shows a warning but continues:
- Filters are imported successfully
- Pattern references are preserved in filter definitions
- You'll see "Pattern not found" in Revit until you manually load the patterns
- Recommended: Always keep .PAT and .XLSX files together

### Q: Can I edit the Excel file before importing?
**A:** Yes! You can:
- ✓ Modify filter names
- ✓ Change colors, line weights
- ✓ Update rule values
- ✓ Add/remove filters
- ⚠️ Don't change the column structure or header names
- ⚠️ Keep the Rules syntax format intact

### Q: Excel vs CSV - which should I use?
**A:** 
- **Excel (.xlsx)** - Recommended! Better formatting, easier to read, supports colors
- **CSV** - Use for legacy systems, scripting, or version control (Git-friendly)
- Both formats contain identical data

### Q: Can I import filters created in older Revit versions?
**A:** Yes! The tool handles API differences automatically. Filters exported from Revit 2023 work perfectly in Revit 2026 and vice versa.

---

## Performance

### Q: How many filters can I copy at once?
**A:** Tested with 100+ filters to 50+ views simultaneously. No practical limit!

### Q: Does it slow down Revit?
**A:** No. Operations are optimized and use Revit API efficiently. Copying 50 filters takes ~5 seconds.

---

## Troubleshooting

### Q: Import says "Success" but filters don't appear in my view
**A:** Check:
1. Are filters enabled? (View → Visibility/Graphics → Filters tab)
2. Is your view using a template that doesn't include these filters?
3. Do the filter categories match elements in your view?

### Q: Filters import but show "Value" instead of actual values
**A:** This was a bug in v1.0.0, fixed in v1.0.1. Update to the latest version.

### Q: "Pattern not found" warnings after import
**A:** The .PAT file wasn't imported or is in a different location. Re-import and ensure the .PAT file is in the same folder as the .XLSX file.

### Q: Custom parameters not created during import
**A:** Make sure you clicked "Yes" in the custom parameters dialog. If you clicked "No", parameters won't be created and filters using them will fail.

---

**For complete licensing information, pricing, and terms:**
👉 **[View Licensing & Pricing Guide](LICENSING.md)**


---

## Tips & Best Practices

### Q: Any tips for organizing filters?
**A:** Yes!
- Use consistent naming: Prefix with discipline (ARCH_, STRUCT_, MEP_)
- Export filter sets to Excel as documentation
- Create master templates with all office standard filters
- Use descriptive names, not "Filter1", "Filter2"

### Q: How to set up filters for coordination meetings?
**A:**
1. Create filter sets for each discipline
2. Export all sets to Excel
3. Share Excel files with coordination team
4. Each discipline imports relevant filters
5. Everyone has identical view setups!

### Q: Can I use this for Revit templates?
**A:** Absolutely! Common workflow:
1. Build perfect filters in test project
2. Export to Excel
3. Import into company template
4. Distribute template to all projects

---

## Still have questions?

**Contact us:** itzikb.bim@gmail.com

**Documentation:** [link]

**Video tutorials:** [link]