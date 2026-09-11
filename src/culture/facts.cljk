(ns culture.facts
  "Country-level regional-culture catalog for Jordan (JOR) -- national
  dishes, protected products, beverages, crafts, festivals and heritage
  sites, per ADR-2607171400 addendum 2 (cloud-itonami-municipality-
  culture-catalog Wave 1, in com-junkawasaki/root). Sibling namespace to
  the `marketentry.facts` / `statute.facts` catalogs of the iso3166
  siblings (ADR-2607141700); city-level counterparts live in the
  cloud-itonami-municipality-* repos.

  Catalog is keyed by UPPERCASE ISO3 (mirrors `statute.facts`); entries
  carry no :culture/municipality (that attribute is city-level only).

  Every entry cites a source URL that was actually fetched and read on
  :culture/retrieved-at -- never fabricated. Summaries state only what the
  cited source confirms. An item not in this table has NO spec-basis, full
  stop; extend `catalog`, do not invent an id/url.")

(def catalog
  "iso3 -> vector of culture entries."
  {"JOR"
   [{:culture/id "jor.dish.mansaf"
     :culture/name "Mansaf"
     :culture/country "JOR"
     :culture/kind :dish
     :culture/summary "Traditional Jordanian dish of lamb cooked in a sauce of fermented dried yogurt and served with rice or bulgur, considered the national dish of Jordan; its traditions were recognized by UNESCO as intangible cultural heritage in 2022."
     :culture/url "https://en.wikipedia.org/wiki/Mansaf"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "jor.dish.maqluba"
     :culture/name "Maqluba"
     :culture/country "JOR"
     :culture/kind :dish
     :culture/summary "Traditional Levantine pilaf of meat, rice and fried vegetables flipped upside-down when served; Jordan is listed among its places of origin alongside Lebanon, Palestine, Syria and Iraq."
     :culture/url "https://en.wikipedia.org/wiki/Maqluba"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "jor.dish.qalayet-bandora"
     :culture/name "Qalayet bandora"
     :culture/country "JOR"
     :culture/kind :dish
     :culture/summary "Simple Levantine dish of tomatoes, onions, hot peppers, olive oil and salt, popular across the Levant and especially in Jordan and Palestine, traditionally prepared during the olive harvest season."
     :culture/url "https://en.wikipedia.org/wiki/Qalayet_bandora"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "jor.beverage.arabic-coffee"
     :culture/name "Arabic coffee"
     :culture/country "JOR"
     :culture/kind :beverage
     :culture/summary "Brewed coffee of Coffea arabica beans, typically cardamom-flavored and served without sugar in small cups; in Jordan the black qahwah sādah 'welcome coffee' remains a traditional sign of respect and hospitality."
     :culture/url "https://en.wikipedia.org/wiki/Arabic_coffee"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "jor.festival.jerash-festival"
     :culture/name "Jerash Festival"
     :culture/country "JOR"
     :culture/kind :festival
     :culture/summary "Annual cultural festival held since 1981 in the Roman theaters of Jerash, Jordan, bringing together Jordanian, Arab and international artists in late July and early August."
     :culture/url "https://en.wikipedia.org/wiki/Jerash_Festival"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "jor.heritage.petra"
     :culture/name "Petra"
     :culture/country "JOR"
     :culture/kind :heritage
     :culture/summary "Ancient Nabataean city in southern Jordan famous for its rock-cut architecture and water conduit systems; a UNESCO World Heritage Site designated in 1985."
     :culture/url "https://en.wikipedia.org/wiki/Petra"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "jor.heritage.wadi-rum"
     :culture/name "Wadi Rum"
     :culture/country "JOR"
     :culture/kind :heritage
     :culture/summary "Valley carved into sandstone and granite in southern Jordan, with dramatic rock formations, ancient petroglyphs and inscriptions; a UNESCO World Heritage Site designated in 2011."
     :culture/url "https://en.wikipedia.org/wiki/Wadi_Rum"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "jor.heritage.madaba-map"
     :culture/name "Madaba Map"
     :culture/country "JOR"
     :culture/kind :heritage
     :culture/summary "6th-century floor mosaic in the early Byzantine church of Saint George in Madaba, Jordan, containing the oldest surviving original cartographic depiction of the Holy Land."
     :culture/url "https://en.wikipedia.org/wiki/Madaba_Map"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}]})

(defn spec-basis [iso3] (get catalog iso3))

(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s)
         missing (remove catalog iso3s)]
     {:requested (count iso3s)
      :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note (str "cloud-itonami-iso3166-jor culture catalog "
                 "(ADR-2607171400 addendum 2, Wave 1): " (count (get catalog "JOR"))
                 " JOR entries, each with a fetched-and-read citation. "
                 "Extend `culture.facts/catalog`, never fabricate an id/url.")})))

(defn by-kind [iso3 kind]
  (filterv #(= (:culture/kind %) kind) (spec-basis iso3)))
