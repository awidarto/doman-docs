# MakeInertiaColumns Command Documentation / Dokumentasi Command MakeInertiaColumns

## English Documentation

### Overview
The `MakeInertiaColumns` command is a custom Laravel Artisan command that generates TanStack Table column definitions from YAML configuration files. This command is designed to automate the creation of table column configurations for Inertia.js applications using Vue 3 and TypeScript.

### Command Signature
```bash
php artisan make:inertia-columns {yamlFile} {outputPath} [options]
```

### Required Arguments
- **yamlFile**: Path to the YAML configuration file (relative to project root)
- **outputPath**: Path where the generated TypeScript file will be saved (relative to project root)

### Available Options
- `--edit-mode=page`: Sets the edit mode for the generated columns (default: "page")
- `--create-mode=page`: Sets the create mode for the generated columns (default: "page")
- `--route-prefix=`: Sets the route prefix for the generated columns
- `--entity-name=`: Sets the entity name for the generated columns
- `--entity-name-lower=`: Sets the lowercase entity name for the generated columns

### YAML Configuration Structure

The command expects a YAML file with the following structure:

```yaml
table:
  - name: "column_name"
    label: "Column Label"
    show: true
  - name: "another_column"
    label: "Another Column"
    show: false

vue:
  - model: "field_name"
    type: "string"
  - model: "number_field"
    type: "integer"
  - model: "flag_field"
    type: "boolean"
```

#### YAML Configuration Details

**Table Section:**
- `name`: The accessor key for the column data
- `label`: The display header text for the column
- `show`: Boolean flag to determine if the column should be included in the output

**Vue Section:**
- `model`: The field name that will be used in the TypeScript interface
- `type`: The data type for TypeScript type mapping

#### Supported Data Types
The command maps YAML types to TypeScript types as follows:
- `integer`, `number` → `number`
- `boolean` → `boolean`
- `string`, `text`, `textarea`, `datetime` → `string`
- Any other type → `any`

### Detailed YAML Structure (Based on Project Example)

The project uses comprehensive YAML configuration files like `manager_controller.yml` with the following structure:

```yaml
table:
  - label: "Name"              # Display label for the column
    name: name                  # Database field name/accessor
    show: true                  # Whether to display in table (true/false)
    search: true                # Whether column is searchable
    sort: false                 # Whether column is sortable
    filter: false               # Whether column has filter
    datatype: text              # Data type (text, date, boolean, image, etc.)
    row_text_alignment: text-left    # CSS alignment class
    column_classes: text-200    # CSS classes for styling
    thClass: ""                 # CSS classes for header
  - label: "Avatar"
    name: avatar
    show: true
    datatype: image             # Special handling for image columns
    column_classes: "text-100 text-center"
  - label: "Email"
    name: email
    show: true
    search: true
    datatype: text
    column_classes: text-250

vue:  
  - model: name                 # TypeScript interface field name
    visible: true               # Whether field is visible in forms
    type: string                # TypeScript type
    default: ""                 # Default value
    im: true                    # Import flag
    ex: true                    # Export flag 
    search: true                # Search capability flag
  - model: email
    visible: true
    type: string
    default: ""
    im: true
    ex: true
    search: true
  - model: useTimeTracker
    visible: true
    type: boolean               # Boolean type example
    default: true
    im: true
    ex: true
    search: true
```

#### Key Features of Project YAML Structure:

1. **Rich Table Configuration**: Each table column includes styling, behavior, and display options
2. **Multiple Data Types**: Support for text, image, date, boolean, and custom types
3. **Search and Filter Options**: Granular control over column searchability and filtering
4. **CSS Integration**: Built-in support for Tailwind CSS classes and custom styling
5. **TypeScript Integration**: Automatic generation of TypeScript interfaces from Vue section

### Generated Output

The command uses a stub template located at `resources/views/stubs/inertia/js/columns.ts.stub` and replaces the following placeholders:

- `{{pl_columns}}`: Generated column definitions
- `{{pl_interface_fields}}`: Generated TypeScript interface fields
- `{{pl_edit_mode}}`: Edit mode value
- `{{pl_create_mode}}`: Create mode value
- `{{pl_route_prefix}}`: Route prefix value
- `{{pl_entity_name}}`: Entity name value
- `{{pl_primary_entity_lower}}`: Lowercase entity name value

### Real-World Example

Using the existing `manager_controller.yml` file in the project:

```bash
# Generate manager columns from existing YAML configuration
php artisan make:inertia-columns resources/models/controllers/directory/manager_controller.yml resources/js/pages/Directory/Manager/columns.ts --route-prefix=directory.manager --entity-name=Manager --entity-name-lower=manager

# Generate with modal edit mode
php artisan make:inertia-columns resources/models/controllers/directory/manager_controller.yml resources/js/pages/Directory/Manager/columns.ts --edit-mode=modal --create-mode=page --route-prefix=directory.manager --entity-name=Manager --entity-name-lower=manager
```

### Example Usage

```bash
# Generate columns from YAML configuration
php artisan make:inertia-columns config/tables/users.yaml resources/js/pages/Users/columns.ts --route-prefix=users --entity-name=User --entity-name-lower=user

# Generate with custom modes
php artisan make:inertia-columns config/tables/products.yaml resources/js/pages/Products/columns.ts --edit-mode=modal --create-mode=page --route-prefix=products --entity-name=Product --entity-name-lower=product
```

### Error Handling

The command includes comprehensive error handling:
- Validates YAML file existence and format
- Creates output directories if they don't exist
- Provides clear error messages for debugging
- Returns appropriate exit codes (0 for success, 1 for error)

### Dependencies

This command requires:
- `symfony/yaml` package for YAML parsing
- Laravel's Console Command base class
- A properly formatted stub template

### Integration with Other Commands

This command works well with other Inertia commands:
- `MakeInertiaForm`: Generates form components from the same YAML file's `form`, `view`, and `vue` sections
  - The `vue` section is now utilized for TypeScript interface generation and additional field definitions
  - Provides type safety and consistency across form components and table columns
- `MakeInertiaCrud`: Generates complete CRUD interfaces using all sections of the YAML

The generated columns file can be imported and used in data table components to provide a consistent table interface throughout your application.

#### Enhanced MakeInertiaForm Integration

The `MakeInertiaForm` command has been enhanced to utilize the `vue` section:

```bash
php artisan make:inertia-form resources/models/controllers/directory/manager_controller.yml \
  --output-path="resources/js/Pages/Admin/Manager/Components" \
  --route-prefix="admin.manager" \
  --model-variable="manager" \
  --entity-name="Manager" \
  --entity-name-lower="manager"
```

This will now generate:
- **TypeScript interfaces** from the `vue` section field definitions
- **Additional form fields** for fields defined in `vue` but not in `form`
- **Proper type mapping** from YAML types to TypeScript types
- **Duplicate field prevention** to avoid conflicts between `form` and `vue` sections

The generated form components will include:
- `{{{pl_vue_interface_fields}}}`: TypeScript interface field definitions
- `{{{pl_vue_additional_fields}}}`: Additional form fields from vue section

---

## Dokumentasi Bahasa Indonesia

### Gambaran Umum
Command `MakeInertiaColumns` adalah perintah Laravel Artisan kustom yang menghasilkan definisi kolom TanStack Table dari file konfigurasi YAML. Command ini dirancang untuk mengotomatisasi pembuatan konfigurasi kolom tabel untuk aplikasi Inertia.js yang menggunakan Vue 3 dan TypeScript.

### Tanda Tangan Command
```bash
php artisan make:inertia-columns {yamlFile} {outputPath} [opsi]
```

### Argumen Wajib
- **yamlFile**: Path ke file konfigurasi YAML (relatif terhadap root proyek)
- **outputPath**: Path tempat file TypeScript yang dihasilkan akan disimpan (relatif terhadap root proyek)

### Opsi yang Tersedia
- `--edit-mode=page`: Mengatur mode edit untuk kolom yang dihasilkan (default: "page")
- `--create-mode=page`: Mengatur mode create untuk kolom yang dihasilkan (default: "page")
- `--route-prefix=`: Mengatur prefix route untuk kolom yang dihasilkan
- `--entity-name=`: Mengatur nama entitas untuk kolom yang dihasilkan
- `--entity-name-lower=`: Mengatur nama entitas huruf kecil untuk kolom yang dihasilkan

### Struktur Konfigurasi YAML

Command ini mengharapkan file YAML dengan struktur sebagai berikut:

```yaml
table:
  - name: "nama_kolom"
    label: "Label Kolom"
    show: true
  - name: "kolom_lain"
    label: "Kolom Lain"
    show: false

vue:
  - model: "nama_field"
    type: "string"
  - model: "field_angka"
    type: "integer"
  - model: "field_flag"
    type: "boolean"
```

#### Detail Konfigurasi YAML

**Seksi Table:**
- `name`: Kunci accessor untuk data kolom
- `label`: Teks header yang ditampilkan untuk kolom
- `show`: Flag boolean untuk menentukan apakah kolom harus disertakan dalam output

**Seksi Vue:**
- `model`: Nama field yang akan digunakan dalam interface TypeScript
- `type`: Tipe data untuk mapping tipe TypeScript

#### Tipe Data yang Didukung
Command ini memetakan tipe YAML ke tipe TypeScript sebagai berikut:
- `integer`, `number` → `number`
- `boolean` → `boolean`
- `string`, `text`, `textarea`, `datetime` → `string`
- Tipe lainnya → `any`

### Output yang Dihasilkan

Command ini menggunakan template stub yang terletak di `resources/views/stubs/inertia/js/columns.ts.stub` dan mengganti placeholder berikut:

- `{{pl_columns}}`: Definisi kolom yang dihasilkan
- `{{pl_interface_fields}}`: Field interface TypeScript yang dihasilkan
- `{{pl_edit_mode}}`: Nilai mode edit
- `{{pl_create_mode}}`: Nilai mode create
- `{{pl_route_prefix}}`: Nilai prefix route
- `{{pl_entity_name}}`: Nilai nama entitas
- `{{pl_primary_entity_lower}}`: Nilai nama entitas huruf kecil

### Contoh Penggunaan

```bash
# Menghasilkan kolom dari konfigurasi YAML
php artisan make:inertia-columns config/tables/users.yaml resources/js/pages/Users/columns.ts --route-prefix=users --entity-name=User --entity-name-lower=user

# Menghasilkan dengan mode kustom
php artisan make:inertia-columns config/tables/products.yaml resources/js/pages/Products/columns.ts --edit-mode=modal --create-mode=page --route-prefix=products --entity-name=Product --entity-name-lower=product
```

### Penanganan Error

Command ini mencakup penanganan error yang komprehensif:
- Memvalidasi keberadaan dan format file YAML
- Membuat direktori output jika belum ada
- Menyediakan pesan error yang jelas untuk debugging
- Mengembalikan kode keluar yang sesuai (0 untuk sukses, 1 untuk error)

### Dependencies

Command ini membutuhkan:
- Package `symfony/yaml` untuk parsing YAML
- Kelas base Laravel Console Command
- Template stub yang terformat dengan benar

### Catatan Implementasi

**Fitur Utama:**
1. **Parsing YAML**: Menggunakan Symfony YAML parser untuk membaca konfigurasi
2. **Generasi Kolom**: Membuat definisi kolom TanStack Table secara otomatis
3. **Interface TypeScript**: Menghasilkan interface TypeScript berdasarkan konfigurasi Vue
4. **Template System**: Menggunakan sistem template dengan placeholder replacement
5. **Directory Management**: Otomatis membuat direktori output jika diperlukan

**Keamanan:**
- Validasi input untuk mencegah path traversal
- Error handling yang robust
- Type checking untuk data YAML

**Performa:**
- Efisien dalam memproses file YAML besar
- Minimal memory footprint
- Fast string replacement operations

### Integrasi dengan Proyek

Command ini terintegrasi dengan baik dengan arsitektur proyek:
- Menggunakan konvensi Laravel untuk Artisan commands
- Kompatibel dengan struktur direktori proyek
- Mendukung workflow development yang ada
- Konsisten dengan pola code generation lainnya

### Troubleshooting

**Masalah Umum:**
1. **File YAML tidak ditemukan**: Pastikan path file YAML benar dan relatif terhadap root proyek
2. **Direktori output tidak dapat dibuat**: Periksa permission sistem file
3. **Template stub tidak ditemukan**: Pastikan file stub ada di `resources/views/stubs/inertia/js/columns.ts.stub`
4. **Format YAML tidak valid**: Validasi syntax YAML menggunakan parser online

**Tips Debugging:**
- Gunakan `--verbose` flag untuk output lebih detail
- Periksa log Laravel untuk error tambahan
- Validasi struktur YAML sebelum menjalankan command
