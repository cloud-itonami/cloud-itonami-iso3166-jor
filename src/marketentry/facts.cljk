(ns marketentry.facts "Jordan market-entry catalog.")
(def catalog
  {"JOR" {:name "Jordan"
          :owner-authority "Government Tenders Department / e-procurement"
          :legal-basis "Government Procurement Bylaw (Bylaw No. 8 of 2022)"
          :national-spec "e-procurement + Companies Control Department registration"
          :provenance "https://www.gtd.gov.jo/"
          :required-evidence ["CCD registration record" "e-procurement registration record" "Tax number record" "Authorized-representative record"]
          :rep-owner-authority "contracting authorities / GTD"
          :rep-legal-basis "Jordanian legal entity registration typically required for public awards"
          :rep-provenance "https://www.gtd.gov.jo/"
          :corporate-number-owner-authority "CCD / ISTD"
          :corporate-number-legal-basis "Company registration / tax number"
          :corporate-number-provenance "https://www.ccd.gov.jo/"}})

(defn spec-basis [iso3] (get catalog iso3))
(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s) missing (remove catalog iso3s)]
     {:requested (count iso3s) :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note "R0 catalog seed"})))
(defn required-evidence-satisfied? [iso3 submitted]
  (when-let [{:keys [required-evidence]} (spec-basis iso3)]
    (= (count required-evidence) (count (filter (set submitted) required-evidence)))))
(defn evidence-checklist [iso3] (:required-evidence (spec-basis iso3) []))
(defn rep-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:rep-owner-authority sb)
      (select-keys sb [:rep-owner-authority :rep-legal-basis :rep-provenance]))))
(defn corporate-number-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:corporate-number-owner-authority sb)
      (select-keys sb [:corporate-number-owner-authority :corporate-number-legal-basis :corporate-number-provenance]))))
