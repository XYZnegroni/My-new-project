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
