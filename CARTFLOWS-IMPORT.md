# Import the CartFlows funnel

Use **cartflows-checkout-funnel.json** for CartFlows import. The older **checkout-template.json** remains an Elementor template and is not the file to select in CartFlows.

## Download and import

1. Open `cartflows-checkout-funnel.json` on GitHub and click **Download raw file** (the down-arrow icon). Download the actual JSON, not the GitHub page saved as HTML.
2. On your WordPress site, activate WooCommerce, Elementor, Elementor Pro, and the CartFlows components that made your supplied export work. Elementor Pro is required for the template's scoped Custom CSS. CartFlows product-selection, quantity, and variation options depend on the features available in your installed CartFlows edition.
3. Open **CartFlows → Funnels** (called **Flows** in some versions), choose its **Import** option, and select `cartflows-checkout-funnel.json`. Use the same import screen that accepted `mili-mitag-gps-tracker.json`. Do not import this file through Elementor's template library.
4. Import it as a new funnel. It contains a **Checkout** step and a **Thank You** step. Do not replace your working funnel until you have checked the new one.
5. Open the new Checkout step's CartFlows settings and assign your own WooCommerce product(s). Save. Product IDs, prices, inventory, gateways, and shipping configuration are deliberately not copied from the reference store.
6. Choose **Edit with Elementor** for the Checkout step. Replace brand, copy, price-summary, ingredient, contact, and image placeholders. Empty Image widgets are present in Navigator; select your Media Library assets and remove the accompanying placeholder headings.
7. Configure real shipping zones, payment methods, and store currency in WooCommerce. Set any CartFlows product/quantity options supported by your installed edition. The exported CartFlows billing-field configuration comes from your supplied working export and can be reviewed in that step's settings.
8. Open the funnel's Checkout step URL, confirm that the assigned products appear, and test a full order on staging with an offline or test payment method. Confirm the Thank You step shows the actual test order. The Elementor buttons scroll to the order section; CartFlows controls the assigned products.

## What changed

- The design now sits inside the full CartFlows funnel envelope from your supplied working export, including its outer JSON-string encoding, `flow_meta`, steps, step metadata, and nested Elementor data.
- The generic `[woocommerce_checkout]` shortcode was replaced with the supplied export's native CartFlows **checkout-form** widget. Its layout is set to one column to suit the reference screenshots.
- The Thank You step uses the supplied export's **order-details-form** widget for dynamic order details.
- Existing site IDs, cached rendered markup, sample order details, unrelated product content, SEO metadata, and unused loop-grid content are excluded. CartFlows must create the new flow and step IDs during import.
- Your original uploaded export has not been published to this repository.

## Validation

The output parses and round-trips through both JSON layers. Its flow and step envelope keys match the supplied export; both embedded Elementor documents parse; IDs are unique within each step. Exactly one CartFlows checkout widget and one dynamic order-details widget are present. The old checkout shortcode is absent. Source-site IDs and rendered caches are absent.

The file was **not imported into WordPress or CartFlows here**, because no configured WordPress/CartFlows runtime is available. Browser rendering, version compatibility, and ordering remain unverified. Matching the supplied export's format is evidence of packaging compatibility, not a guarantee that your site's importer or checkout will succeed. A successful import also does not assign a product or configure your store automatically.
