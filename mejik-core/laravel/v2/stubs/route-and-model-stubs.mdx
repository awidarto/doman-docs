# Enhanced Route and Model Stubs Documentation

## Overview

This document describes the enhanced route stubs and model stubs that have been improved to support modern development patterns, including comment-based identification for selective modification/removal and comprehensive hierarchical data structures.

## Route Stubs

### 1. Primary Routes (`primary-routes.stub`)

**Location**: `resources/views/stubs/inertia/routes/primary-routes.stub`

#### Features

- **Comment Identifiers**: Routes are wrapped with `BEGIN:` and `END:` comments for easy identification and selective modification
- **Comprehensive CRUD**: Full CRUD operations with additional bulk operations
- **Middleware Integration**: Includes authentication and verification middleware
- **Extended Operations**: Export/Import, bulk operations, status management, and history tracking

#### Generated Route Structure

```php
// BEGIN:admin.users - User CRUD Routes
Route::middleware(['auth', 'verified'])->prefix('admin/users')->name('admin.users.')->group(function () {
    // Main dashboard/index route
    Route::get('/', [UserController::class, 'index'])->name('index');
    
    // BEGIN:admin.users.user - Primary entity routes
    Route::prefix('user')->name('user.')->group(function () {
        // Standard CRUD
        Route::get('/', [UserController::class, 'indexPrimary'])->name('index');
        Route::get('/create', [UserController::class, 'createPrimary'])->name('create');
        Route::post('/', [UserController::class, 'storePrimary'])->name('store');
        Route::get('/{id}', [UserController::class, 'showPrimary'])->name('show');
        Route::get('/{id}/edit', [UserController::class, 'editPrimary'])->name('edit');
        Route::put('/{id}', [UserController::class, 'updatePrimary'])->name('update');
        Route::patch('/{id}', [UserController::class, 'updatePrimary'])->name('patch');
        Route::delete('/{id}', [UserController::class, 'destroyPrimary'])->name('destroy');
        
        // Bulk operations
        Route::post('/bulk-delete', [UserController::class, 'bulkDestroyPrimary'])->name('bulk.destroy');
        Route::post('/bulk-update', [UserController::class, 'bulkUpdatePrimary'])->name('bulk.update');
        
        // Export/Import routes
        Route::get('/export', [UserController::class, 'exportPrimary'])->name('export');
        Route::post('/import', [UserController::class, 'importPrimary'])->name('import');
        
        // Status management routes
        Route::patch('/{id}/status', [UserController::class, 'updateStatusPrimary'])->name('status.update');
        Route::get('/{id}/history', [UserController::class, 'historyPrimary'])->name('history');
    });
    // END:admin.users.user
    
    {{secondary_routes}} // Placeholder for optional secondary routes
});
// END:admin.users
```

#### Placeholders

- `{{route_name_prefix}}`: Route name prefix (e.g., 'admin.users')
- `{{controller_name}}`: Human-readable controller name (e.g., 'User')
- `{{route_prefix}}`: URL prefix (e.g., 'admin/users')
- `{{controller_class}}`: Controller class name (e.g., 'UserController')
- `{{primary_entity_route}}`: Primary entity route segment (e.g., 'user')
- `{{secondary_routes}}`: Optional secondary routes content

### 2. Secondary Routes (`secondary-routes.stub`)

**Location**: `resources/views/stubs/inertia/routes/secondary-routes.stub`

#### Features

- **Master-Detail Pattern**: Designed for hierarchical or related entity management
- **Relationship Management**: Attach/detach operations for related entities
- **Bulk Operations**: Bulk attach/detach functionality
- **Ordering Support**: Move up/down and reorder operations for ordered relationships

#### Generated Route Structure

```php
// BEGIN:admin.users.profile - Secondary entity routes (Master-Detail pattern)
Route::prefix('profile')->name('profile.')->group(function () {
    // Secondary entity CRUD routes
    Route::get('/', [UserController::class, 'indexSecondary'])->name('index');
    Route::get('/create', [UserController::class, 'createSecondary'])->name('create');
    Route::post('/', [UserController::class, 'storeSecondary'])->name('store');
    Route::get('/{id}', [UserController::class, 'showSecondary'])->name('show');
    Route::get('/{id}/edit', [UserController::class, 'editSecondary'])->name('edit');
    Route::put('/{id}', [UserController::class, 'updateSecondary'])->name('update');
    Route::patch('/{id}', [UserController::class, 'updateSecondary'])->name('patch');
    Route::delete('/{id}', [UserController::class, 'destroySecondary'])->name('destroy');
    
    // Master-Detail relationship routes
    Route::get('/by-master/{masterId}', [UserController::class, 'indexSecondaryByMaster'])->name('by-master');
    Route::post('/attach-to-master', [UserController::class, 'attachToMaster'])->name('attach-master');
    Route::delete('/detach-from-master/{id}', [UserController::class, 'detachFromMaster'])->name('detach-master');
    
    // Bulk operations for secondary entities
    Route::post('/bulk-delete', [UserController::class, 'bulkDestroySecondary'])->name('bulk.destroy');
    Route::post('/bulk-attach', [UserController::class, 'bulkAttachToMaster'])->name('bulk.attach');
    Route::post('/bulk-detach', [UserController::class, 'bulkDetachFromMaster'])->name('bulk.detach');
    
    // Ordering/Sorting routes (for ordered details)
    Route::post('/{id}/move-up', [UserController::class, 'moveSecondaryUp'])->name('move-up');
    Route::post('/{id}/move-down', [UserController::class, 'moveSecondaryDown'])->name('move-down');
    Route::post('/reorder', [UserController::class, 'reorderSecondary'])->name('reorder');
});
// END:admin.users.profile
```

#### Placeholders

- `{{route_name_prefix}}`: Route name prefix
- `{{secondary_entity_route}}`: Secondary entity route segment
- `{{controller_class}}`: Controller class name

#### Selective Route Management

The comment identifiers allow for easy selective modification or removal of route groups:

```bash
# Find and modify specific route group
grep -n "BEGIN:admin.users" routes/web.php
grep -n "END:admin.users" routes/web.php

# Remove specific route group programmatically
sed -i '/BEGIN:admin.users/,/END:admin.users/d' routes/web.php
```

## Model Stubs

### Available Model Stubs

1. **Generic Model** (`model.stub`): Universal model with placeholders for both MongoDB and SQL
2. **MongoDB Model** (`model-mongodb.stub`): MongoDB-specific with proper imports and casts
3. **SQL Model** (`model-sql.stub`): Standard Laravel Eloquent model

### Key Features

#### 1. Modern MongoDB/SQL Compatibility

- Uses `$table` property for both MongoDB and SQL (modern MongoDB driver alignment)
- Proper handling of `id` field (no more `_id` confusion)
- Appropriate imports for each database type

#### 2. Comprehensive Hierarchical Support

All model stubs include extensive hierarchical functionality:

**Relationships:**
- `parent()`: Get parent item
- `children()`: Get direct children
- `descendants()`: Get all descendants recursively
- `ancestors()`: Get all ancestors recursively
- `siblings()`: Get siblings (same parent)

**Scopes:**
- `scopeRoot()`: Get root items (no parent)
- `scopeByLevel()`: Get items by hierarchy level
- `scopeActive()`: Get active items
- `scopeHierarchical()`: Get hierarchically ordered items
- `scopeWithHierarchy()`: Get with hierarchy relationships loaded

**Helper Methods:**
- `getDepthLevel()`: Calculate hierarchy depth
- `getHierarchicalPath()`: Get full path from root
- `isAncestorOf()`: Check if item is ancestor of another
- `isDescendantOf()`: Check if item is descendant of another
- `isRoot()`: Check if item is root
- `isLeaf()`: Check if item is leaf (no children)
- `moveTo()`: Move item to new parent (with circular reference prevention)

**Static Methods:**
- `getTree()`: Get complete tree structure
- `getFlatHierarchy()`: Get flattened hierarchy for dropdowns

**Lifecycle Hooks:**
- Auto-calculation of hierarchy levels
- Automatic children level updates when parent changes

#### 3. MongoDB Model Specific Features (`model-mongodb.stub`)

```php
use App\Casts\MongoUTC;
use App\Casts\MongoBoolean;
use MongoDB\Laravel\Eloquent\Model as Eloquent;

protected function casts(): array
{
    return [
        'created_at' => MongoUTC::class,
        'updated_at' => MongoUTC::class,
        'createdAt' => MongoUTC::class,
        'updatedAt' => MongoUTC::class,
        // Additional field casts
    ];
}

protected $guarded = ['id']; // Modern MongoDB uses 'id' not '_id'
```

#### 4. SQL Model Specific Features (`model-sql.stub`)

```php
use Illuminate\Database\Eloquent\Model;

protected function casts(): array
{
    return [
        'created_at' => 'datetime',
        'updated_at' => 'datetime',
        // Additional field casts
    ];
}
```

#### 5. Placeholders

All model stubs support these placeholders:

- `{{namespace_path}}`: Namespace path (e.g., `\Directory`)
- `{{model_imports}}`: Additional imports
- `{{model_name}}`: Model class name
- `{{base_class}}`: Base class (Model or Eloquent)
- `{{soft_deletes_trait}}`: SoftDeletes trait if needed
- `{{soft_deletes_import}}`: SoftDeletes import if needed
- `{{connection_name}}`: Database connection name
- `{{table_name}}`: Table/collection name
- `{{fillable_fields}}`: Fillable fields array content
- `{{guarded_fields}}`: Guarded fields array content
- `{{timestamps_property}}`: Timestamp property setting
- `{{date_casts}}`: Date casting definitions
- `{{field_casts}}`: Additional field casts
- `{{hidden_fields}}`: Hidden fields array content
- `{{additional_methods}}`: Additional methods

### Usage Examples

#### MongoDB Model Generation

```php
// Will use model-mongodb.stub
$modelContent = str_replace([
    '{{namespace_path}}' => '\Directory',
    '{{model_name}}' => 'User',
    '{{connection_name}}' => 'mongodb',
    '{{table_name}}' => 'users',
    '{{fillable_fields}}' => "'name',\n        'email',\n        'status'",
    '{{field_casts}}' => "'status' => 'string',\n            'is_active' => MongoBoolean::class,",
], $stub);
```

#### SQL Model Generation

```php
// Will use model-sql.stub  
$modelContent = str_replace([
    '{{namespace_path}}' => '\Admin',
    '{{model_name}}' => 'Category',
    '{{connection_name}}' => 'mysql',
    '{{table_name}}' => 'categories',
    '{{fillable_fields}}' => "'name',\n        'slug',\n        'parent_id'",
    '{{field_casts}}' => "'is_active' => 'boolean',",
], $stub);
```

### Hierarchical Data Usage

#### Building Trees

```php
// Get complete tree structure
$tree = Category::getTree();

// Get flattened hierarchy for dropdown
$options = Category::getFlatHierarchy('name', '— ');

// Get items by level
$rootItems = Category::root()->get();
$level2Items = Category::byLevel(2)->get();
```

#### Working with Individual Items

```php
$category = Category::find(1);

// Get hierarchy information
$level = $category->getDepthLevel();
$path = $category->getHierarchicalPath(); // "Root > Parent > Current"
$isRoot = $category->isRoot();
$isLeaf = $category->isLeaf();

// Move item
$category->moveTo($newParent); // Automatically prevents circular references

// Check relationships
$category->isAncestorOf($otherCategory);
$category->isDescendantOf($parentCategory);
```

## Integration with Code Generation

These enhanced stubs work seamlessly with the existing code generation commands and provide:

1. **Consistent Route Structure**: Predictable route patterns with comprehensive operations
2. **Selective Management**: Easy identification and modification of specific route groups
3. **Database Agnostic**: Proper model generation for both MongoDB and SQL databases
4. **Hierarchical Support**: Built-in support for tree-like data structures
5. **Modern Patterns**: Aligned with current Laravel and MongoDB driver conventions

The comment identifiers in routes enable automated tooling to selectively modify or remove specific route groups without affecting other parts of the route file, making it perfect for dynamic CRUD generation and maintenance.
