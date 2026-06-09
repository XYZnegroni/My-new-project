# EcoGarden-AI: Inventory-Linked Personalized Plant Recommendation System

## Summary
EcoGarden-AI is a data-driven retail solution that connects a customer's specific garden environment with a garden center's live inventory system. By utilizing geospatial data analysis and advanced recommendation algorithms, the system suggests the perfect plants that are guaranteed to thrive in the customer's yard *and* are currently available on the store shelves, maximizing retail sales while eliminating plant care failures.

## Background
The gardening and retail nursery industry suffers from a unique misalignment between customer desires and store inventory management, leading to significant pain points for both sides.

### 🔴 The Buyer's Pain Points (Customers)
* **The "Intention vs. Reality" Gap:** Beginners often buy plants based purely on their beautiful appearance at the store, only to have them wither within weeks because the plant was unsuited for their yard's specific sunlight, soil, or winter climate.
* **Overwhelming Choices & Seasonality:** Customers rarely know *when* and *where* to plant. Buying a frost-sensitive plant in late autumn leads to immediate failure and frustration, causing them to give up gardening altogether.

### 🔴 The Seller's Pain Points (Garden Centers)
* **High Perishable Waste (Shrinkage):** Live plants are highly perishable. Missing the peak sales window or overstocking results in massive plant disposal costs and direct profit loss.
* **Low Customer Lifetime Value (LTV):** When customers fail to keep their plants alive, they lose confidence, stop purchasing, and rarely return to the store.
* **Staff Dependency:** Providing high-quality, expert advice for hundreds of plant varieties requires highly trained staff, which is increasingly difficult due to labor shortages.

---

## How is it used?
EcoGarden-AI creates a seamless bridge between the customer's home and the garden center's retail floor.

### 📱 User Experience (The Buyer)
1. **Garden Mapping:** The customer drops a pin on Google Maps to register their yard's coordinates and logs currently owned plants on a simple grid layout.
2. **Instant Environmental Assessment:** The AI automatically fetches local climate zones, historical sunlight hours, and seasonal data.
3. **In-Store Scanning:** At the garden center, the user scans a plant's barcode or takes a photo. The AI instantly calculates a "Match Score" based on their yard's compatibility and tells them exactly *where* to plant it.

### 📈 Retail Operations (The Seller)
1. **Dynamic Stock Promotion:** The AI recommendation engine automatically applies a "boost weight" to overstocked or high-margin items that match the customer's yard profile.
2. **Proactive Demand Forecasting:** Aggregated anonymous data from local yards allows store managers to predict upcoming seasonal demands (e.g., a high demand for shade-loving plants in a specific neighborhood) and optimize procurement.

```python
def calculate_recommendation_score(plant_profile, yard_profile, inventory_status):
    # Base compatibility calculated from sunlight, climate zone, and season
    base_compatibility = evaluate_compatibility(plant_profile, yard_profile)
    
    # B2B Booster: Increase ranking if the garden center has high stock levels
    if inventory_status['stock_level'] > 100:
        inventory_booster = 1.2  # 20% boost to clear overstock
    elif inventory_status['is_high_margin']:
        inventory_booster = 1.15 # 15% boost for high-profit items
    else:
        inventory_booster = 1.0
        
    return base_compatibility * inventory_booster

## Data sources and AI methods
To achieve high-precision recommendations and automated business logic, EcoGarden-AI utilizes a multimodal data pipeline:

* **Geospatial & Climate Data:** Hardiness zones, local frost dates, and structural shade modeling retrieved via Google Maps API and regional meteorological databases.
* **Live POS/ERP Inventory Data:** Real-time stock levels and profit margins synced from the garden center's inventory management system (initially prototyped using structured data stored on Google Drive).
* **AI Methods:**
  * **Computer Vision (CNN):** Image classification to instantly recognize plant species from smartphone photos in the store.
  * **Collaborative Filtering & Knowledge Graphs:** Relational mapping to recommend plant combinations (companion planting) based on what is already growing in the user's garden.
  * **Weighted Recommendation Algorithms:** Linear and logistic scoring functions to balance ecological fit with business profit margins.

| Data Input | Processing Layer | Output Action |
| ----------- | ----------- | ----------- |
| GPS / Satellite Images | Climate Data Extraction | Filters out plants that won't survive the winter |
| Live POS Stock Data | Business Weight Injection | Promotes overstocked items in the user's feed |
| User's Current Garden Map | Knowledge Graph Matching | Suggests companion plants (e.g., underplanting) |

## Challenges
* **The "Black Box" of Soil Quality:** While climate and sunlight can be estimated remotely, soil pH and drainage require manual input or sensor data for 100% accuracy.
* **Overfitting to Overstock:** If the algorithm prioritizes overstocked items too aggressively, it may compromise the ecological match score, leading to plant failure and breaking user trust. The balance must be carefully fine-tuned.
* **Perishable Data Delays:** Garden center inventory shifts rapidly. Delays in data syncing could result in recommending an item that just sold out minutes prior.

## What next?
* **Direct E-Commerce Integration:** Allow users to click "Buy & Reserve for Pickup" directly from their automated seasonal garden plan.
* **Smart Alert Notifications:** Push notification systems reminding users when to water, fertilize, or prune based on their live garden log, triggering consistent repeat visits to the partner garden center.
* **MLOps Migration:** Move from the Google Drive prototype to an automated, low-latency cloud infrastructure (AWS/GCP) to support real-time inventory synchronization across multi-store retail chains.

## Acknowledgments
* Inspired by the pragmatic art of machine learning and the customer data model of the **K-Ruoka web store** case in the Elements of AI course.
* Built using Python, `scikit-learn` for predictive scoring, and Open-Source Computer Vision libraries.
