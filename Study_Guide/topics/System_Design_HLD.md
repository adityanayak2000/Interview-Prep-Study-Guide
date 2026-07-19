# System Design HLD (router)

> 🚪 [Start](../START_HERE.md) · 🗺️ [Map](../README.md) · 🏢 [Companies](../companies/README.md) · 📚 [Library](../library/README.md) · 🔍 [Find](../FIND.md)

**Software / Product track** · Light for campus freshers; deeper for product senior loops.

## Why it matters
Product companies ask capacity / API / storage sketches. Semiconductor Tier S rarely needs full HLD — prioritize [Systems Interview](Systems_Interview.md) instead.

## Concept map
- Requirements (functional vs non-functional) → API → data model → components → scale.  
- Building blocks: load balancer, cache, DB (SQL vs NoSQL), queue, CDN.  
- Consistency vs availability (CAP awareness).  
- Estimate: QPS, storage, bandwidth (order-of-magnitude).  

## Practice direction
- Design: URL shortener, news feed, rate limiter (tie to LLD).  
- Always state assumptions aloud.

## Boss Sheet
[HLD Boss Sheet](https://drive.google.com/file/d/1YClCcB5e1tq1dNNnXeDQUnibCjCLykYI/view)

## Resource Panel
- [System Design Questions Ebook](https://drive.google.com/file/d/1RZGN4VZgFc5w8LRkhpoXfpmtfB_n9hzY/view)
- [donnemartin / system-design-primer](https://github.com/donnemartin/system-design-primer)
- [awesome-system-design-resources](https://github.com/ashishps1/awesome-system-design-resources)
- [SystemDesignInterviewPreparationSeries](https://github.com/Sunchit/SystemDesignInterviewPreparationSeries)
- [HLD Primer](https://systemdesignschool.io/primer)
- Interview Prep §System Design: [🎯 Interview Prep](../../🎯%20Interview%20Prep%20Resources.md)  
- Pair with: [OOPs_LLD](OOPs_LLD.md) · [Software archetype](../archetypes/Software_Product_SDE.md)  
- [00_INDEX](../00_INDEX.md)
