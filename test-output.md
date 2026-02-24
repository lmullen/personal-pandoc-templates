---
title: "Test Document for Default LaTeX Template"
#subtitle: "Verifying Typography, Structure, and Layout"
author: Lincoln Mullen
#date: February 23, 2026
fontsize: 10pt
---

This document serves as a test of the default LaTeX template used with Pandoc. Its purpose is to exercise the major structural and typographic features that the template supports, including headings at multiple levels, hyperlinks, footnotes, block quotations, and lists. The content itself is drawn from the history of digital humanities and computational methods in historical research, topics that happen to be useful for filling out a document of roughly one thousand words.

### This is a sample h3

Digital humanities as a field has roots stretching back to the mid-twentieth century, when Father Roberto Busa began work on the *Index Thomisticus*, a concordance of the works of Thomas Aquinas.[^busa] That project, which required decades of collaboration with IBM, is often cited as the founding moment of humanities computing. Since then, the methods available to humanities scholars have expanded enormously, encompassing text mining, network analysis, spatial analysis, and much more.

[^busa]: For an overview of Busa's project and its legacy, see Steven E. Jones, *Roberto Busa, S.J., and the Emergence of Humanities Computing* (New York: Routledge, 2016).

# Text Analysis and Distant Reading

## Foundations of Computational Text Analysis

The analysis of texts at scale has become one of the most prominent applications of computational methods in the humanities. Franco Moretti's concept of "distant reading" proposed that scholars could learn new things about literary history by analyzing thousands of texts rather than performing close readings of individual works.[^moretti] This idea proved both influential and controversial, sparking debates about the relationship between quantitative and qualitative methods that continue to this day.

[^moretti]: Franco Moretti, *Distant Reading* (London: Verso, 2013). See also the responses collected in the [Stanford Literary Lab](https://litlab.stanford.edu/) pamphlet series.

Topic modeling, a technique borrowed from machine learning, gained popularity among historians and literary scholars in the early 2010s. Tools like [MALLET](https://mimno.github.io/Mallet/) made it possible for researchers without extensive programming backgrounds to discover latent themes in large collections of documents.[^topic] The results were not always easy to interpret, but the method opened new avenues for exploring archives and corpora.

[^topic]: David M. Blei, "Probabilistic Topic Models," *Communications of the ACM* 55, no. 4 (2012): 77--84.

### Word Embeddings and Neural Methods

More recently, word embedding models such as Word2Vec and GloVe have enabled researchers to study semantic change over time. By training models on historical corpora divided into temporal slices, scholars can track how the meanings of words shifted across decades or centuries.[^embeddings] These methods raise important questions about bias, representativeness, and the relationship between language and culture.

[^embeddings]: For a historical application, see Ryan Heuser, "Word Vectors in the Eighteenth Century," available at the [Stanford Literary Lab](https://litlab.stanford.edu/).

## Challenges in Text Analysis

Several challenges confront scholars who work with large text corpora:

1. **Optical character recognition** (OCR) quality varies dramatically across digitized collections, introducing noise that can distort results.
2. **Corpus construction** decisions---which texts to include, how to sample, how to handle duplicates---shape findings in ways that are not always transparent.
3. **Interpretation** of computational results requires domain expertise; statistical patterns do not explain themselves.
4. **Reproducibility** remains difficult when tools, data, and methods change rapidly.

These are not merely technical problems. They are epistemological challenges that require humanists to think carefully about what computational methods can and cannot reveal.

# Spatial and Network Analysis

## Mapping the Past

Geographic information systems (GIS) and spatial analysis have transformed how historians study the past. Projects like the [Digital Scholarship Lab](https://dsl.richmond.edu/) at the University of Richmond have produced atlases and interactive maps that make spatial patterns in American history visible in new ways. The *American Panorama* project, for instance, offers visualizations of the forced migration of enslaved people, the movement of immigrants, and the redlining of American cities.[^panorama]

[^panorama]: Robert K. Nelson, et al., *American Panorama: An Atlas of United States History* (University of Richmond, 2015--), [https://dsl.richmond.edu/panorama/](https://dsl.richmond.edu/panorama/).

### Spatial Humanities in Practice

Spatial analysis is not limited to mapping. Scholars have used spatial methods to study the distribution of churches in early modern cities, the spread of disease in nineteenth-century epidemics, and the geographic dimensions of literary production. The key insight is that space is not merely a backdrop to historical events but an active force that shapes human experience.

## Networks and Relationships

Network analysis offers another lens for studying historical relationships. By modeling people, organizations, and institutions as nodes connected by edges, scholars can identify patterns of influence, communication, and exchange that are difficult to see through traditional methods.[^network] The [Mapping the Republic of Letters](http://republicofletters.stanford.edu/) project at Stanford, for example, visualized the correspondence networks of Enlightenment thinkers, revealing unexpected connections and intellectual communities.

[^network]: See Scott Weingart, "Demystifying Networks," *Journal of Digital Humanities* 1, no. 1 (2011).

# Code and Computation

## Code Examples

Computational methods in the humanities often require writing code for data processing and analysis. Below are examples in two languages commonly used in digital humanities research.

A Go program to count word frequencies in a text:

```go
package main

import (
	"fmt"
	"strings"
)

func wordFrequencies(text string) map[string]int {
	freqs := make(map[string]int)
	for _, word := range strings.Fields(strings.ToLower(text)) {
		word = strings.Trim(word, ".,;:!?\"'()-")
		if word != "" {
			freqs[word]++
		}
	}
	return freqs
}

func main() {
	text := "the purpose of computing is insight not numbers"
	for word, count := range wordFrequencies(text) {
		fmt.Printf("%s: %d\n", word, count)
	}
}
```

An R script to visualize publication counts over time:

```r
library(ggplot2)

# Simulated data: digital humanities publications by year
publications <- data.frame(
  year = 2000:2025,
  count = c(12, 15, 18, 22, 28, 35, 42, 55, 70, 88,
            110, 135, 165, 200, 240, 290, 340, 400,
            460, 530, 610, 700, 780, 870, 960, 1050)
)

ggplot(publications, aes(x = year, y = count)) +
  geom_line(linewidth = 0.8) +
  geom_point(size = 2) +
  labs(
    title = "Growth of Digital Humanities Publications",
    x = "Year",
    y = "Number of Publications"
  ) +
  theme_minimal()
```

# Reflections on Method

The proliferation of digital methods in the humanities raises fundamental questions about the nature of evidence, argument, and interpretation. Computational approaches do not replace traditional humanistic inquiry; rather, they supplement it, offering new perspectives on familiar questions and sometimes posing entirely new ones.

> The purpose of computing is insight, not numbers.
>
> ---Richard Hamming[^hamming]

[^hamming]: Richard W. Hamming, *Numerical Methods for Scientists and Engineers* (New York: McGraw-Hill, 1962).

As digital humanities continues to mature, its practitioners must navigate tensions between:

- Quantitative rigor and interpretive nuance
- Scalability and attention to particularity
- Technical innovation and humanistic values
- Open access and the protection of sensitive materials

These tensions are productive rather than paralyzing. They push scholars to articulate their assumptions, justify their methods, and engage with audiences both within and beyond the academy. The best digital humanities work does not merely apply tools to texts; it asks why those tools matter and what they reveal about the human past.

### Looking Ahead

The future of computational methods in the humanities will likely be shaped by advances in large language models, the growing availability of digitized primary sources, and the continued development of open-source tools and infrastructure. Whether these developments fulfill their promise will depend not on the technology alone but on the communities of scholars who use it thoughtfully and critically.
