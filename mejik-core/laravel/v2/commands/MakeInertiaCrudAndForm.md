# MakeInertiaCrud & MakeInertiaForm Commands Documentation

## English Documentation

---

## MakeInertiaCrud Command

### Overview
The `MakeInertiaCrud` command is a comprehensive Laravel Artisan command that generates a complete Inertia.js CRUD system. It creates controllers, models, Vue.js pages, routes, and integrates with the column and form generation commands to provide a full-featured management system.

### Command Signature
```bash
php artisan make:inertia-crud {name} [options]
```

### Required Arguments
- **name**: The name of the controller (e.g., `Product`, `UserProfile`)

### Required Options
- **--route**: The base URI for the module (e.g., `catalog/products`) - **MANDATORY**
- **--yml**: The path to the YAML file for column generation - **MANDATORY**

### Optional Parameters
- `--primary-create-mode=page`: The mode for creating the primary entity (`page` or `dialog`)
- `--primary-edit-mode=page`: The mode for editing the primary entity (`page` or `dialog`)
- `--primary-show-mode=page`: The mode for showing the primary entity (`page` or `dialog`)
- `--ns=App`: The namespace for the controller (e.g., `App\\Modules\\Catalog`)
- `--model=`: The model class name
- `--primary-model=`: The primary model class name
- `--secondary-model=`: The secondary model class name (optional for hierarchical structures)
- `--page-namespace=`: Custom page namespace for Vue components
- `--system-name=`: Custom system name for display
- `--mongo`: Generate MongoDB models instead of SQL models
- `--force`: Overwrite existing files
- `--cleanup`: Remove generated files for this module

### Generated Components

#### 1. Controller
**Location**: `app/Http/Controllers/{namespace}/{Name}Controller.php`

**Stub Template**: `resources/views/stubs/inertia/class/controller.stub`

**Template Placeholders**:
- `{namespace_path}`: Directory path for the namespace
- `{namespace_full}`: Complete PHP namespace
- `{controller_name}`: Controller class name
- `{primary_model_class}`: Primary model class with full namespace
- `{page_namespace}`: Vue page namespace path
- `{route_prefix}`: Route prefix (dots notation)
- `{primary_entity_name}`: Primary entity name (singular)
- `{system_name}`: Display name for the system
- `{secondary_model_import}`: Import statement for secondary model (if exists)
- `{secondary_model_assignment}`: Assignment of secondary model class
- `{secondary_entity_name_assignment}`: Secondary entity name assignment
- `{secondary_model_fields_config}`: Configuration for secondary model fields
- `{secondary_validation_rules_config}`: Validation rules for secondary model
- `{statistics_implementation}`: Statistics calculation implementation
- `{secondary_model_methods}`: Additional methods for secondary model

#### 2. Models
**Location**: `app/Models/{ModelName}.php`

**Stub Template**: `resources/views/stubs/inertia/class/model.stub`

**Template Placeholders**:
- `{model_name}`: Model class name
- `{namespace_path}`: Namespace path for the model
- `{table_name}`: Database table/collection name
- `{model_imports}`: Import statements (different for SQL vs MongoDB)
- `{base_class}`: Base class (`Model` for SQL, `Eloquent` for MongoDB)
- `{table_property}`: Property name (`table` for SQL, `collection` for MongoDB)
- `{soft_deletes_trait}`: SoftDeletes trait (for MongoDB only)
- `{connection_name}`: Database connection name

#### 3. Vue Components

**Generated Pages**:
- `Index.vue`: Main listing page with data table
- `Create.vue`: Create form page (if primary-create-mode=page)
- `CreateForm.vue`: Create form component
- `CreateDialog.vue`: Create dialog modal
- `Edit.vue`: Edit form page (if primary-edit-mode=page)
- `EditForm.vue`: Edit form component  
- `EditDialog.vue`: Edit dialog modal
- `Show.vue`: Detail view page
- `ShowDialog.vue`: Detail view modal
- `columns.ts`: TanStack Table column definitions

**Vue Template Placeholders**:
- `{pl_page_namespace}`: Page namespace for imports
- `{pl_route_prefix}`: Route prefix for navigation
- `{pl_system_name}`: System display name
- `{pl_entity_name}`: Entity name (singular, PascalCase)
- `{pl_entity_name_lower}`: Entity name (lowercase)
- `{pl_model_variable}`: Model variable name (camelCase)
- `{pl_title_field}`: Default title field name
- `{pl_secondary_model_sidebar}`: Sidebar content for hierarchical structures
- `{pl_secondary_model_sidebar_comment}`: Comment for sidebar positioning
- `{pl_main_content_class}`: CSS class for main content area

**Form-Specific Placeholders**:
- `{pl_form_fields}`: Generated form field HTML
- `{pl_form_models}`: Form model definitions
- `{pl_sidebar_content}`: Sidebar content for forms
- `{pl_form_data}`: Form data initialization
- `{pl_form_data_with_values}`: Form data with default values
- `{pl_parent_info}`: Parent item information display
- `{pl_save_button_text}`: Save button text
- `{pl_has_status_field}`: Status field availability flag
- `{pl_secondary_model_props}`: Props for secondary model
- `{pl_computed_properties}`: Computed properties
- `{pl_additional_methods}`: Additional Vue methods
- `{pl_watch_statements}`: Vue watch statements
- `{pl_default_values}`: Default form values

**Show Page Placeholders**:
- `{pl_status_badge}`: Status badge HTML
- `{pl_author_info}`: Author information display
- `{pl_meta_info}`: Metadata information
- `{pl_content_display}`: Content display area
- `{pl_tags_display}`: Tags display area
- `{pl_statistics_display}`: Statistics display
- `{pl_status_display}`: Status information
- `{pl_published_display}`: Published date display

**Index Page Placeholders**:
- `{pl_columns_import_path}`: Import path for columns file
- `{pl_primary_entity_name}`: Primary entity name
- `{pl_primary_entity_name_lower}`: Primary entity name (lowercase)
- `{pl_primary_entity_lower}`: Primary entity (lowercase)
- `{pl_add_item_route}`: Route for creating new items
- `{pl_create_mode}`: Create mode (page/dialog)
- `{pl_edit_mode}`: Edit mode (page/dialog)
- `{pl_show_mode}`: Show mode (page/dialog)
- `{pl_statistics_cards}`: Statistics cards HTML section
- `{pl_grid_item_template}`: Grid view item template
- `{pl_modal_components}`: Modal components inclusion
- `{pl_modal_imports}`: Modal component imports
- `{pl_type_imports}`: TypeScript type imports
- `{pl_modal_props_interface}`: Modal props in Props interface
- `{pl_modal_logic}`: Modal handling logic
- `{pl_event_listeners}`: Event bus listeners
- `{pl_mounted_logic}`: Logic for onMounted hook
- `{pl_unmounted_logic}`: Logic for onUnmounted hook

#### 4. Routes
**Location**: `routes/app/custom.php`

**Generated Route Structure**:
```php
// {ControllerName} CRUD Routes
Route::prefix('{route}')->name('{route-prefix}.')->group(function () {
    Route::get('/', [ControllerClass::class, 'index'])->name('index');

    // Primary entity routes
    Route::prefix('{primary-entity}')->name('{primary-entity}.')->group(function () {
        Route::get('/', [ControllerClass::class, 'indexPrimary'])->name('index');
        Route::get('/create', [ControllerClass::class, 'createPrimary'])->name('create');
        Route::post('/', [ControllerClass::class, 'storePrimary'])->name('store');
        Route::get('/{id}', [ControllerClass::class, 'showPrimary'])->name('show');
        Route::get('/{id}/edit', [ControllerClass::class, 'editPrimary'])->name('edit');
        Route::put('/{id}', [ControllerClass::class, 'updatePrimary'])->name('update');
        Route::delete('/{id}', [ControllerClass::class, 'destroyPrimary'])->name('destroy');
    });

    // Secondary entity routes (if secondary model exists)
    Route::prefix('{secondary-entity}')->name('{secondary-entity}.')->group(function () {
        Route::get('/create', [ControllerClass::class, 'createSecondary'])->name('create');
        Route::post('/', [ControllerClass::class, 'storeSecondary'])->name('store');
        Route::get('/{id}/edit', [ControllerClass::class, 'editSecondary'])->name('edit');
        Route::put('/{id}', [ControllerClass::class, 'updateSecondary'])->name('update');
        Route::delete('/{id}', [ControllerClass::class, 'destroySecondary'])->name('destroy');
    });
});
```

### Example Usage

#### Basic CRUD System
```bash
php artisan make:inertia-crud ProductCatalog \
  --route=catalog/products \
  --yml=resources/models/controllers/catalog/product_controller.yml \
  --primary-model=App\\Models\\Product
```

#### Advanced CRUD with Hierarchy
```bash
php artisan make:inertia-crud DocumentManagement \
  --route=dms/documents \
  --yml=resources/models/controllers/dms/document_controller.yml \
  --primary-model=App\\Models\\Document \
  --secondary-model=App\\Models\\DocumentCategory \
  --ns=App\\Modules\\DMS \
  --primary-create-mode=dialog \
  --primary-edit-mode=dialog
```

#### MongoDB CRUD System
```bash
php artisan make:inertia-crud UserProfile \
  --route=core/users \
  --yml=resources/models/controllers/core/user_controller.yml \
  --primary-model=App\\Models\\User \
  --mongo
```

#### Cleanup Generated Files
```bash
php artisan make:inertia-crud ProductCatalog --cleanup
```

---

## MakeInertiaForm Command

### Overview
The `MakeInertiaForm` command generates Vue.js form components from YAML configuration files. It creates Create, Edit, and Show (view) components with proper form field mappings and model bindings.

### Command Signature
```bash
php artisan make:inertia-form {yamlFile} [options]
```

### Required Arguments
- **yamlFile**: Path to the YAML configuration file

### Required Options
- **--output-path**: Output directory path for generated components

### Optional Parameters
- `--route-prefix=`: Route prefix for form actions
- `--model-variable=`: Variable name for the model object
- `--entity-name=`: Entity name for naming conventions
- `--entity-name-lower=`: Lowercase entity name

### YAML Configuration Structure

The command expects YAML with `form` and `view` sections:

```yaml
form:
  - label: "Full Name"
    name: fullName
    model: name
    create: true
    edit: true
    type: text
    default: ""
    validator: "required"
    
view:
  - label: "Full Name"
    name: displayName
    model: name
    visible: true
    type: text
```

### Generated Components

#### 1. CreateForm.vue
**Stub Template**: `resources/views/stubs/inertia/js/CreateForm.vue.stub`

**Template Placeholders**:
- `{{{pl_form_fields}}}`: Generated form field HTML elements
- `{{{pl_form_models}}}`: Form model initialization
- `{{pl_store_route}}`: Route for storing new records
- `{{pl_model_variable}}`: Model variable name

#### 2. EditForm.vue
**Stub Template**: `resources/views/stubs/inertia/js/EditForm.vue.stub`

**Template Placeholders**:
- `{{{pl_form_fields}}}`: Generated form field HTML elements
- `{{{pl_form_models}}}`: Form model initialization with existing values
- `{{pl_update_route}}`: Route for updating records
- `{{pl_model_variable}}`: Model variable name

#### 3. ShowView.vue
**Stub Template**: `resources/views/stubs/inertia/js/ShowView.vue.stub`

**Template Placeholders**:
- `{{{pl_view_fields}}}`: Generated view field HTML elements
- `{{pl_model_variable}}`: Model variable name

### Field Generation Logic

#### Form Fields
Generated HTML structure:
```html
<!-- {field.name} | {field.model} -->
<div class="mb-3">
    <label for="{field.name}" class="form-label">{field.label}</label>
    <input type="text" id="{field.name}" v-model="form.{field.model}" class="form-control" />
</div>
```

#### Form Models
Generated model structure:
```javascript
{field.model}: props.object?.{field.model} || '{field.default}',
```

#### View Fields
Generated view structure:
```html
<div class="mb-3">
    <label class="form-label">{field.label}</label>
    <div>{{ object.{field.model} }}</div>
</div>
```

### Example Usage

#### Basic Form Generation
```bash
php artisan make:inertia-form resources/models/controllers/core/user_controller.yml \
  --output-path=resources/js/pages/Core/User \
  --route-prefix=core.user \
  --model-variable=user \
  --entity-name=User \
  --entity-name-lower=user
```

#### Integration with CRUD Generation
The form command is automatically called by `make:inertia-crud` when a YAML file is provided:

```bash
# This automatically calls make:inertia-form internally
php artisan make:inertia-crud ProductCatalog \
  --route=catalog/products \
  --yml=resources/models/controllers/catalog/product_controller.yml
```

---

## Dokumentasi Bahasa Indonesia

---

## Command MakeInertiaCrud

### Gambaran Umum
Command `MakeInertiaCrud` adalah perintah Laravel Artisan yang komprehensif untuk menghasilkan sistem CRUD Inertia.js lengkap. Command ini membuat controller, model, halaman Vue.js, route, dan terintegrasi dengan command generasi kolom dan form untuk menyediakan sistem manajemen berfitur lengkap.

### Tanda Tangan Command
```bash
php artisan make:inertia-crud {name} [opsi]
```

### Argumen Wajib
- **name**: Nama controller (contoh: `Product`, `UserProfile`)

### Opsi Wajib
- **--route**: URI dasar untuk modul (contoh: `catalog/products`) - **WAJIB**
- **--yml**: Path ke file YAML untuk generasi kolom - **WAJIB**

### Parameter Opsional
- `--primary-create-mode=page`: Mode untuk membuat entitas utama (`page` atau `dialog`)
- `--primary-edit-mode=page`: Mode untuk mengedit entitas utama (`page` atau `dialog`)
- `--primary-show-mode=page`: Mode untuk menampilkan entitas utama (`page` atau `dialog`)
- `--ns=App`: Namespace untuk controller (contoh: `App\\Modules\\Catalog`)
- `--model=`: Nama kelas model
- `--primary-model=`: Nama kelas model utama
- `--secondary-model=`: Nama kelas model sekunder (opsional untuk struktur hierarkis)
- `--page-namespace=`: Namespace halaman kustom untuk komponen Vue
- `--system-name=`: Nama sistem kustom untuk tampilan
- `--mongo`: Menghasilkan model MongoDB alih-alih model SQL
- `--force`: Menimpa file yang sudah ada
- `--cleanup`: Menghapus file yang dihasilkan untuk modul ini

### Komponen yang Dihasilkan

#### 1. Controller
**Lokasi**: `app/Http/Controllers/{namespace}/{Name}Controller.php`

**Template Stub**: `resources/views/stubs/inertia/class/controller.stub`

**Placeholder Template**:
- `{namespace_path}`: Path direktori untuk namespace
- `{namespace_full}`: Namespace PHP lengkap
- `{controller_name}`: Nama kelas controller
- `{primary_model_class}`: Kelas model utama dengan namespace lengkap
- `{page_namespace}`: Path namespace halaman Vue
- `{route_prefix}`: Prefix route (notasi titik)
- `{primary_entity_name}`: Nama entitas utama (tunggal)
- `{system_name}`: Nama tampilan untuk sistem
- `{secondary_model_import}`: Statement import untuk model sekunder (jika ada)
- `{secondary_model_assignment}`: Assignment kelas model sekunder
- `{secondary_entity_name_assignment}`: Assignment nama entitas sekunder
- `{secondary_model_fields_config}`: Konfigurasi untuk field model sekunder
- `{secondary_validation_rules_config}`: Aturan validasi untuk model sekunder
- `{statistics_implementation}`: Implementasi kalkulasi statistik
- `{secondary_model_methods}`: Method tambahan untuk model sekunder

#### 2. Model
**Lokasi**: `app/Models/{ModelName}.php`

**Template Stub**: `resources/views/stubs/inertia/class/model.stub`

**Placeholder Template**:
- `{model_name}`: Nama kelas model
- `{namespace_path}`: Path namespace untuk model
- `{table_name}`: Nama tabel/koleksi database
- `{model_imports}`: Statement import (berbeda untuk SQL vs MongoDB)
- `{base_class}`: Kelas dasar (`Model` untuk SQL, `Eloquent` untuk MongoDB)
- `{table_property}`: Nama properti (`table` untuk SQL, `collection` untuk MongoDB)
- `{soft_deletes_trait}`: Trait SoftDeletes (hanya untuk MongoDB)
- `{connection_name}`: Nama koneksi database

#### 3. Komponen Vue

**Halaman yang Dihasilkan**:
- `Index.vue`: Halaman listing utama dengan tabel data
- `Create.vue`: Halaman form create (jika primary-create-mode=page)
- `CreateForm.vue`: Komponen form create
- `CreateDialog.vue`: Modal dialog create
- `Edit.vue`: Halaman form edit (jika primary-edit-mode=page)
- `EditForm.vue`: Komponen form edit
- `EditDialog.vue`: Modal dialog edit
- `Show.vue`: Halaman detail view
- `ShowDialog.vue`: Modal detail view
- `columns.ts`: Definisi kolom TanStack Table

### Contoh Penggunaan

#### Sistem CRUD Dasar
```bash
php artisan make:inertia-crud ProductCatalog \
  --route=catalog/products \
  --yml=resources/models/controllers/catalog/product_controller.yml \
  --primary-model=App\\Models\\Product
```

#### CRUD Lanjutan dengan Hierarki
```bash
php artisan make:inertia-crud DocumentManagement \
  --route=dms/documents \
  --yml=resources/models/controllers/dms/document_controller.yml \
  --primary-model=App\\Models\\Document \
  --secondary-model=App\\Models\\DocumentCategory \
  --ns=App\\Modules\\DMS \
  --primary-create-mode=dialog \
  --primary-edit-mode=dialog
```

#### Pembersihan File yang Dihasilkan
```bash
php artisan make:inertia-crud ProductCatalog --cleanup
```

---

## Command MakeInertiaForm

### Gambaran Umum
Command `MakeInertiaForm` menghasilkan komponen form Vue.js dari file konfigurasi YAML. Command ini membuat komponen Create, Edit, dan Show (view) dengan pemetaan field form dan binding model yang tepat.

### Tanda Tangan Command
```bash
php artisan make:inertia-form {yamlFile} [opsi]
```

### Argumen Wajib
- **yamlFile**: Path ke file konfigurasi YAML

### Opsi Wajib
- **--output-path**: Path direktori output untuk komponen yang dihasilkan

### Parameter Opsional
- `--route-prefix=`: Prefix route untuk aksi form
- `--model-variable=`: Nama variabel untuk objek model
- `--entity-name=`: Nama entitas untuk konvensi penamaan
- `--entity-name-lower=`: Nama entitas huruf kecil

### Struktur Konfigurasi YAML

Command ini mengharapkan YAML dengan seksi `form` dan `view`:

```yaml
form:
  - label: "Nama Lengkap"
    name: fullName
    model: name
    create: true
    edit: true
    type: text
    default: ""
    validator: "required"
    
view:
  - label: "Nama Lengkap"
    name: displayName
    model: name
    visible: true
    type: text
```

### Komponen yang Dihasilkan

#### 1. CreateForm.vue
**Template Stub**: `resources/views/stubs/inertia/js/CreateForm.vue.stub`

#### 2. EditForm.vue
**Template Stub**: `resources/views/stubs/inertia/js/EditForm.vue.stub`

#### 3. ShowView.vue
**Template Stub**: `resources/views/stubs/inertia/js/ShowView.vue.stub`

### Logika Generasi Field

#### Field Form
Struktur HTML yang dihasilkan:
```html
<!-- {field.name} | {field.model} -->
<div class="mb-3">
    <label for="{field.name}" class="form-label">{field.label}</label>
    <input type="text" id="{field.name}" v-model="form.{field.model}" class="form-control" />
</div>
```

#### Model Form
Struktur model yang dihasilkan:
```javascript
{field.model}: props.object?.{field.model} || '{field.default}',
```

#### Field View
Struktur view yang dihasilkan:
```html
<div class="mb-3">
    <label class="form-label">{field.label}</label>
    <div>{{ object.{field.model} }}</div>
</div>
```

### Contoh Penggunaan

#### Generasi Form Dasar
```bash
php artisan make:inertia-form resources/models/controllers/core/user_controller.yml \
  --output-path=resources/js/pages/Core/User \
  --route-prefix=core.user \
  --model-variable=user \
  --entity-name=User \
  --entity-name-lower=user
```

#### Integrasi dengan Generasi CRUD
Command form secara otomatis dipanggil oleh `make:inertia-crud` ketika file YAML disediakan:

```bash
# Ini secara otomatis memanggil make:inertia-form secara internal
php artisan make:inertia-crud ProductCatalog \
  --route=catalog/products \
  --yml=resources/models/controllers/catalog/product_controller.yml
```

---

## Integrasi Sistem

### Workflow Lengkap

1. **Persiapan YAML**: Buat file konfigurasi YAML dengan struktur `table`, `form`, dan `view`
2. **Generasi CRUD**: Jalankan `make:inertia-crud` untuk membuat sistem lengkap
3. **Penyesuaian**: Sesuaikan controller, model, dan komponen Vue sesuai kebutuhan
4. **Migrasi Database**: Buat dan jalankan migrasi database
5. **Testing**: Test fungsionalitas CRUD

### Best Practices

1. **Penamaan Konsisten**: Gunakan konvensi penamaan yang konsisten untuk model, controller, dan route
2. **YAML Terstruktur**: Organisir file YAML dengan baik untuk maintainability
3. **Namespace Hierarkis**: Gunakan namespace yang mencerminkan struktur aplikasi
4. **Mode Fleksibel**: Pilih mode (page vs dialog) berdasarkan UX requirements
5. **Validasi Lengkap**: Implementasikan validasi yang komprehensif di controller
6. **Error Handling**: Implement proper error handling di Vue components
7. **Security**: Pastikan authorization dan validation di controller

### Troubleshooting

**Masalah Umum:**
1. **File YAML tidak valid**: Pastikan syntax YAML benar
2. **Namespace conflict**: Periksa namespace yang sudah ada
3. **Template stub tidak ditemukan**: Pastikan semua stub template tersedia
4. **Permission error**: Periksa permission direktori output
5. **Route conflict**: Pastikan route prefix tidak bertabrakan

**Tips Debugging:**
- Gunakan `--force` untuk overwrite file yang ada saat testing
- Periksa log Laravel untuk error detail
- Gunakan `--cleanup` untuk reset dan mulai ulang
- Validasi struktur YAML sebelum generate
- Test dengan konfigurasi sederhana terlebih dahulu

---

## Recent Updates & Modern Patterns

### Updated Vue.js Stubs

All Vue.js stub files have been updated to match current working patterns in the project:

#### **Create.vue & Edit.vue Pattern**
- Uses modern Card-based layout with shadcn/ui components
- Integrates with separate form components for better reusability
- Includes proper TypeScript interfaces and error handling
- Uses vue-sonner for toast notifications

#### **Form Component Architecture**
- **CreateForm.vue**: Standalone form component for create operations
- **EditForm.vue**: Standalone form component for edit operations  
- **ShowView.vue**: Display component for viewing entity details

#### **Generated Form Fields**
The form generation now supports:
- **Input Types**: text, textarea, password, email, number
- **Validation**: Automatic required field marking with `*`
- **Error Handling**: Individual field error display
- **Modern Styling**: Using shadcn/ui Input/Textarea components

#### **Form Field Generation Pattern**
```html
<!-- Generated form field example -->
<div class="space-y-2">
    <Label for="fieldName">Field Label <span class="text-red-500">*</span></Label>
    <Input type="text" id="fieldName" v-model="form.fieldModel" placeholder="Enter Field Label..." :class="{ 'border-red-500': form.errors.fieldModel }" />
    <div v-if="form.errors.fieldModel" class="text-sm text-red-600">
        {{ form.errors.fieldModel }}
    </div>
</div>
```

#### **View Field Generation Pattern**
```html
<!-- Generated view field example -->
<div class="space-y-2">
    <Label class="text-sm font-medium text-muted-foreground">Field Label</Label>
    <div class="text-sm">
        {{ object.fieldModel || 'Not specified' }}
    </div>
</div>
```

#### **Model Form Generation**
Improved form model generation with proper default values:
```javascript
// For different field types
stringField: '',
numberField: 0,
booleanField: false,
arrayField: [],
objectField: {}
```

### New Placeholders Added

#### **Create/Edit Page Placeholders**:
- `{{pl_entity_name}}`: Entity name for dynamic component imports
- `{{pl_create_form_props}}`: Props interface for create form
- `{{pl_edit_form_props}}`: Props interface for edit form
- `{{pl_form_component_props}}`: Props for form components
- `{{pl_view_component_props}}`: Props for view components

### YAML Configuration Enhancement

The system now better handles YAML field configurations:
- **Form Fields**: Checks `create` and `edit` flags to determine inclusion
- **View Fields**: Respects `visible` flag for display
- **Field Types**: Enhanced support for different input types
- **Validation**: Automatic parsing of validator rules
- **Default Values**: Intelligent default value assignment based on field type

### Integration Workflow

1. **YAML Structure**: Uses three main sections:
   - `table`: For data table column definitions
   - `form`: For create/edit form fields
   - `view`: For display/show page fields

2. **Component Generation**: Creates reusable form components that can be used in:
   - Page-based forms (Create.vue, Edit.vue)
   - Dialog/modal forms (future implementation)
   - Custom form layouts

3. **Modern Stack**: Fully integrated with current project patterns:
   - shadcn/ui component library
   - TypeScript interfaces
   - Tailwind CSS styling
   - Vue 3 Composition API
   - Inertia.js form handling

