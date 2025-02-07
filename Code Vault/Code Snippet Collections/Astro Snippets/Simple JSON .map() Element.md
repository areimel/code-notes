```jsx
---
const stats = [
  {
    percentage: "32%",
    description:
      "faster growth for aligned organizations",
    linkName: "Global News Wire",
    linkUrl: "https://www.globalnews.com/wire/32-faster-growth-for-aligned-organizations/",
  },
  {
    percentage: "36%",
    description:
      "higher customer retention rates",
    linkName: "ZoomInfo, MarketingProfs",
    linkUrl: "https://www.zoominfo.com/blog/customer-retention-rates-and-growth-rates-are-closely-related",
  },
  {
    percentage: "20%",
    description:
      "annual growth rate for aligned companies",
    linkName: "Aberdeen Research",
    linkUrl: "https://www.aberdeen.com/en/research/articles/2022/03/22/aligned-companies-grow-faster-than-unaligned-ones",
  }
];
---

<div class="grid grid-cols-3 gap-16">
  {
	stats.map((item) => (
	  <div class="card text-center">
		<div class="card-number text-5xl font-bold text-yellow-400 ">
		  {item.percentage}
		</div>
		<div class="text-3xl font-bold balanced-text">
		  {item.description}
		</div>
		<div class="mt-4 text-sm text-slate-400 underline">
		  <a href="#">{item.linkName}</a>
		</div>
	  </div>
	))
  }
  
</div>
```