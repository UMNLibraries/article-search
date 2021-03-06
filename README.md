# Article Search

Known item article search suggestions based on cached metadata

### Demo notes
Viewing article https://onlinelibrary.wiley.com/doi/10.1002/brb3.981
10.1002/brb3.981

References:
- Amano, M., Kohno, M., Nagata, O., Taniguchi, M., Sora, S., & Sato, H. (2011).
  Intraoperative continuous monitoring of evoked facial nerve electromyograms in
  acoustic neuroma surgery. Acta Neurochirurgica, 153(5), 1059–1067.
  https://doi.org/10.1007/s00701-010-0937-6
- Colletti, V., Fiorino, F., Policante, Z., & Bruni, L. (1997). Intraoperative
  monitoring of facial nerve antidromic potentials during acoustic neuroma
  surgery. Acta Oto‐Laryngologica, 117(5), 663–669.
  https://doi.org/10.3109/00016489709113457
- Electrical stimulation-based nerve location prediction for cranial nerve VII
  localization in acoustic neuroma surgery Dilok Puanhvuan,Sorayouth
  Chumnanvej,Yodchanan Wongsawa ISSN: 21623279 , 2162-3279; DOI:
  10.1002/brb3.981 Brain and behavior. , 2018, (0), p.e00981
- Marsland, T. P., & Evans, S. (1987). Dielectric measurements with an
  open‐ended coaxial probe. IEE Proceedings H ‐ Microwaves, Antennas and
  Propagation, 134(4), 341–349. https://doi.org/10.1049/ip-h-2.1987.0068
- McComas, A. J., Fawcett, P. R. W., Campbell, M. J., & Sica, R. E. P. (1971).
  Electrophysiological estimation of the number of motor units within a human
  muscle. Journal of Neurology, Neurosurgery & Psychiatry, 34(2), 121–131.
  https://doi.org/10.1136/jnnp.34.2.121
- Roundy, N., Delashaw, J. B., & Cetas, J. S. (2012). Preoperative
  identification of the facial nerve in patients with large cerebellopontine
  angle tumors using high‐density diffusion tensor imaging: Clinical article.
  Journal of Neurosurgery, 116(4), 697–702.
  https://doi.org/10.3171/2011.12.JNS111404
- Teudt, I. U., Nevel, A. E., Izzo, A. D., Walsh, J. T., & Richter, C.‐P.
  (2007). Optical stimulation of the facial nerve: a new monitoring technique?
  The Laryngoscope, 117(9), 1641–1647.
  https://doi.org/10.1097/MLG.0b013e318074ec00
- Wells, J., Kao, C., Mariappan, K., Albea, J., Jansen, E. D., Konrad, P., &
  Mahadevan‐Jansen, A. (2005). Optical stimulation of neural tissue in vivo.
  Optics Letters, 30(5), 504–506. https://doi.org/10.1364/OL.30.000504
- Zhang, Y., Chen, Y., Zou, Y., Zhang, W., Zhang, R., Liu, X., … Liu, H. (2013).
  Facial nerve preservation with preoperative identification and intraoperative
  monitoring in large vestibular schwannoma surgery. Acta Neurochirurgica,
  155(10), 1857–1862. https://doi.org/10.1007/s00701-013-1815-9


### Notes & Local info
(For internal use)
#### Janus search logs - analyze query length
Using `jq`, long search strings can be retrieved from UMN Janus search logs
Related: https://github.com/UMNLibraries/janus-deploy
```shell
# Assuming a directory with uncompressed Janus redirect logs
# These are linewise JSON objects, not valid JSON as a complete file

# Get all search queries > 100 characters
cat redirect.json* | jq -r 'select(.event.query.target == "MncatDiscovery")|(select(.event.query.search|length > 100))|.event.query.search'

# Tab separated output of search strings and their character length (unicode codepoints)
cat redirect.json* |jq -r 'select(.event.query.target == "MncatDiscovery")|(.event.query.search + "\t" + (.event.query.search|length|tostring))'
```

### Environment Variables
* `ELASTICSEARCH_URL`: specify the search index to connect to, defaults to
  `http://localhost:9200` if unset
* `ELASTICSEARCH_VERBOSE`: Enable verbose logging from the Elasticsearch client
