<div align="center">
  <img src="prevent_zero_sales/static/description/icon.png" width="100" />

  # Prevent Zero Sales

  **Odoo 18.0 Community** · Sales · `OPL-1`

  Blocks confirmation of sales orders and customer invoices with zero/negative
  values, duplicate lines or insufficient stock.
</div>

---

## The problem

Sales teams confirm orders with a price of `0.00`, a duplicated product line, or
a quantity larger than what is actually in stock. The error is only caught in
accounting or at delivery — when it is expensive to fix.

## What this module does

Adds a configurable validation layer on **Sales Orders** and **Customer
Invoices**, blocking confirmation when a line is invalid.

| Feature | Description |
|---|---|
| **Stock validation** | Blocks confirmation when a line exceeds the product's forecasted stock. |
| **Zero / negative values** | Rejects lines with quantity or price `<= 0`. |
| **Duplicate lines** | Optionally prevents the same product appearing twice in one document. |
| **Real-time warnings** | A banner appears on the form as soon as a line breaks a rule — before saving. |
| **Invoice-level check** | Same validation on invoices, skipping lines already validated at sales order level. |
| **Granular config** | Rules configurable per company and per product type (storable, consumable, service). |

## Screenshots

<div align="center">
  <img src="prevent_zero_sales/static/description/main_1.png" width="80%" />
  <img src="prevent_zero_sales/static/description/main_2.png" width="80%" />
  <img src="prevent_zero_sales/static/description/main_3.png" width="80%" />
</div>

## Installation

```bash
# Copy the module into your Odoo addons path
cp -r prevent_zero_sales /path/to/odoo/addons/

# Restart Odoo and update the apps list, then install "Prevent Zero Sales"
```

**Dependencies:** `account`, `sale_management`, `sale_stock`

## Configuration

`Settings → Sales → Prevent Zero Sales` — enable the rules you need per company
and choose which product types each rule applies to.

## Tech notes

- Validation hooks into `action_confirm()` on `sale.order` and `action_post()` on `account.move`.
- Real-time feedback implemented as an OWL component on the order form.
- Includes automated tests under `prevent_zero_sales/tests/`.

## Documentation

Full documentation: [`prevent_zero_sales/README.md`](prevent_zero_sales/README.md) ·
Changelog: [`prevent_zero_sales/changelog.md`](prevent_zero_sales/changelog.md)

## License & author

`OPL-1` — commercial module by
[Consultores Odoo Colombia](https://consultoresodoocolombia.odoo.com/).
Developed by **Juan Carlos Arias Botero**.
