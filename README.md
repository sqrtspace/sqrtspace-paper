# The Ubiquity of Space-Time Simulation in Modern Computing: From Theory to Practice

This repository contains the academic paper exploring how Ryan Williams' 2025 theoretical result, TIME[t] ⊆ SPACE[√(t log t)], manifests in real-world computing systems.

## Paper

**Title**: The Ubiquity of Space-Time Simulation in Modern Computing: From Theory to Practice  
**Author**: David H. Friedel Jr., Founder, MarketAlly LLC (USA) & MarketAlly Pte. Ltd. (Singapore)  
**Status**: Submitted to arXiv (needing endorsement)  



## Abstract

Ryan Williams' 2025 result demonstrates that any time-bounded algorithm can be simulated using only O(√(t log t)) space, establishing a fundamental limit on the space-time relationship in computation. This paper bridges the gap between this theoretical breakthrough and practical computing systems. Through controlled experiments and analysis of production systems, we show that space-time tradeoffs following the √n pattern are ubiquitous across databases, machine learning frameworks, and distributed systems. However, we find that practical constant factors range from 100× to 10,000×, primarily due to memory hierarchies and I/O overhead.

## Related Repositories

- **[Experiments & Code](https://github.com/sqrtspace/sqrtspace-experiments)**: Full implementation, experiments, and interactive dashboard
- **[Interactive Dashboard](https://github.com/sqrtspace/sqrtspace-experiments/tree/main/dashboard)**: Streamlit app for exploring space-time tradeoffs

## Key Findings

1. **Experimental validation**:
   - Checkpointed sorting: 375-627× slowdown for √n space reduction
   - Real LLM inference (Ollama): 18.3× slowdown for √n context chunking
   - Stream processing: 30× speedup with sliding windows (less memory = faster!)
   - SQLite: Counterintuitive faster performance with smaller caches on modern SSDs

2. **Production system analysis**:
   - SQLite (billions of deployments): Buffer pools sized at √(database_size)
   - Flash Attention (GPT-4, etc.): O(n²) → O(n) memory enabling 10× longer contexts
   - PostgreSQL & Apache Spark: √n patterns in buffer pools and shuffle operations

3. **Theory vs practice gap**:
   - Williams predicts √n slowdown, we observe 100-10,000× due to memory hierarchies
   - L1 cache: ~1ns, RAM: ~100ns, SSD: ~100μs, HDD: ~10ms
   - Modern hardware can invert predictions (bandwidth bottlenecks)

4. **Practical framework**:
   - When beneficial: Streaming data, sequential access, distributed systems
   - When harmful: Interactive apps, random access, small datasets
   - Interactive dashboard and tools for practitioners

## Building the Paper

```bash
# Compile the paper
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex

# Compile two-page summary
pdflatex two_page_summary.tex
```

## Citation

Once published on arXiv:
```bibtex
@article{friedel2025ubiquity,
  title={The Ubiquity of Space-Time Simulation in Modern Computing: From Theory to Practice},
  author={Friedel Jr., David H.},
  journal={arXiv preprint arXiv:25XX.XXXXX},
  year={2025}
}
```

## Reading Order

1. **Quick Overview**: Read `executive_summary.md` (2 pages)
2. **Technical Summary**: Read `two_page_summary.tex` (2 pages, compile to PDF)
3. **Full Paper**: Read `main.tex` (26 pages, compile to PDF)
4. **Try It Yourself**: Visit the [experiments repository](https://github.com/sqrtspace/sqrtspace-experiments)

## Contact

- **Email**: dfriedel@marketally.ai
- **Organization**: [MarketAlly LLC](https://marketally.com)

## License

This paper is licensed under CC BY 4.0. You may share and adapt the material with proper attribution.

## Acknowledgments

This work was carried out independently as part of early-stage R&D at MarketAlly LLC and MarketAlly Pte. Ltd. We acknowledge the use of large language models for drafting assistance.