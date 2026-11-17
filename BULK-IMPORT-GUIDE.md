# Magenda Store — Bulk Product Import

Use the CSV template in `bulk-products-template.csv`.

## Required columns
- `sku`: unique product code. Required; existing SKU updates the matching product.
- `name`: product name.
- `category`: category name. A category is created automatically if it does not exist.
- `price`: selling price in EGP. Must be zero or greater.

## Optional columns
- `brand`
- `description`
- `short_description`
- `compare_at_price`
- `stock_quantity` (defaults to 0)
- `image_url` (public image URL)
- `is_active` (true/false, 1/0, yes/no, نعم; defaults to true)
- `is_featured` (true/false, 1/0, yes/no, نعم; defaults to false)

## Import behavior
- Save the CSV as UTF-8.
- Keep the first row as the exact header row from the template.
- Use a unique SKU for every product. Re-importing a SKU updates that product rather than creating a duplicate.
- The admin importer processes rows in batches of 100.
- Invalid rows (missing SKU, name, category, or valid price; negative stock/price) are skipped.
- Images are referenced by URL in this first version; image file upload/storage will be added as a separate feature.
