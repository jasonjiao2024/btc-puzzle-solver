# Bitcoin Puzzle Progressive Solver

An advanced statistical solver for Bitcoin puzzle challenges using progressive refinement, Hamming distance analysis, and intelligent sampling strategies.

## 🎯 Overview

This solver is designed for the [Bitcoin Puzzle Challenge](https://privatekeys.pw/puzzles/bitcoin-puzzle-tx), which presents a series of Bitcoin addresses with known private key ranges but unknown exact keys. The challenge involves finding private keys for addresses containing significant Bitcoin balances.

### Key Features

- **Progressive Refinement**: Multi-level granularity approach (10% → 5% → 1% → 0.1% → 0.01%)
- **Statistical Analysis**: Hamming distance-based evaluation with entropy analysis
- **Enhanced Metrics**: Gradient analysis, bit significance scoring, pattern consistency
- **Memory Efficiency**: Avoids redundant sampling of previously explored keys
- **Multiprocessing**: Parallel evaluation across CPU cores
- **Google Colab Support**: Cloud execution with Google Drive integration
- **Checkpoint System**: Resume interrupted searches automatically
- **Historical Intelligence**: Uses data from previously solved puzzles

## 🧮 Current Configuration

- **Target Puzzle**: #71
- **Target Address**: `1PWo3JeB9jrGwfHDNpdGK54CRas7fsVzXU`
- **Search Range**: `2^70` to `2^71 - 1`

## 🔬 Technical Approach

### Statistical Evaluation
The solver evaluates private key ranges using multiple metrics:

- **Hamming Distance**: Bit-level differences between generated and target HASH160
- **Gradient Analysis**: Rate of change across key ranges
- **Bit Significance**: Which bit positions consistently match target
- **Pattern Consistency**: Correlation between bit patterns
- **Entropy Analysis**: Distribution randomness assessment

### Progressive Refinement Strategy
1. **Level 0 (10%)**: Divide search space into 10 segments
2. **Level 1 (5%)**: Refine to 20 segments  
3. **Level 2 (1%)**: Further refine to 100 segments
4. **Level 3 (0.1%)**: Ultra-fine with 1,000 segments
5. **Level 4+ (0.01%+)**: Extreme precision exploration

### Intelligent Sampling
- Historical puzzle solution analysis
- Bit-pattern aware sampling
- Edge case prioritization (0-5% and 95-100% ranges)
- Complementary sampling to avoid redundancy

## 🚀 Installation & Usage

### Local Installation

```bash
# Clone the repository
git clone https://github.com/jasonjiao2024/bitcoin-puzzle-progressive-solver.git
cd bitcoin-puzzle-progressive-solver

# Install required packages
pip install pycryptodome ecdsa base58 numpy

# Run the solver
python puzzle_solver.py
```

### Google Colab Usage

1. Upload the script to Google Colab
2. The script will automatically:
   - Install required packages
   - Mount Google Drive for checkpoint storage
   - Begin progressive search

### Requirements

- Python 3.7+
- Libraries: `pycryptodome`, `ecdsa`, `base58`, `numpy`
- Minimum 8GB RAM recommended
- Multiple CPU cores for optimal performance

## 📊 Performance Metrics

### Search Efficiency
- **Samples per cycle**: 1M - 10M depending on granularity level
- **Memory usage**: ~2-4GB for key tracking
- **Checkpoint frequency**: Every cycle completion
- **Resume capability**: Instant restart from last checkpoint

### Expected Performance
- **Level 0-2**: Fast exploration of major regions
- **Level 3+**: Intensive analysis of promising areas
- **Adaptive thresholds**: Dynamic adjustment based on findings

## 🔧 Configuration Options

Key parameters can be adjusted in the script:

```python
# Puzzle Configuration
PUZZLE_ID = 71
TARGET_ADDRESS = "1PWo3JeB9jrGwfHDNpdGK54CRas7fsVzXU"

# Statistical Parameters
FIXED_SAMPLE_COUNT = 1000000
HAMMING_THRESHOLD = 52

# Score Weights
STAT_SCORE_WEIGHTS = {
    'min_hamming': 0.55,
    'density_good': 0.25,
    'avg_hamming': 0.05,
    'std_dev_penalty': 0.02,
    'hamming_gradient': 0.08,
    'bit_significance': 0.03,
    'pattern_consistency': 0.02
}
```

## 📈 Progress Tracking

The solver provides detailed progress information:

- Current granularity level and completion percentage
- Best Hamming distance found
- Exploration statistics
- Enhanced metric analysis
- Historical performance data

## 🎉 Success Detection

When the correct private key is found:
- Automatic verification against target address
- WIF (Wallet Import Format) generation
- Result file creation with full details
- Checkpoint cleanup

## ⚠️ Important Disclaimers

### Educational Purpose
This solver is intended for:
- Educational exploration of cryptographic concepts
- Research into Bitcoin's elliptic curve cryptography
- Understanding statistical search methodologies
- Academic study of large-scale optimization problems

### Responsible Use
- Only use on designated puzzle challenges
- Respect computational resource limits
- Consider environmental impact of intensive computation
- Follow applicable laws and regulations

### No Guarantees
- Success is not guaranteed for any puzzle
- Computational requirements may be extreme
- Consider opportunity costs of extended searches

## 💝 Support

### Donations Welcome
If this solver has been helpful for your research, education, or puzzle-solving endeavors, consider supporting the project:

**Bitcoin Address**: `bc1qct9mx2qhj0alzuem0fflhx53arte3q5m0mn5hu`


## 📝 License

This project is released under the MIT License. See `LICENSE` file for details.

## 🔗 References

- [Bitcoin Puzzle Challenge](https://privatekeys.pw/puzzles/bitcoin-puzzle-tx)
- [Bitcoin.org - Technical Overview](https://bitcoin.org/en/developer-guide)
- [ECDSA and Bitcoin](https://en.bitcoin.it/wiki/Elliptic_Curve_Digital_Signature_Algorithm)
  
**⚡ Remember**: The Bitcoin puzzle challenges are extremely difficult by design. This solver represents a sophisticated approach but cannot guarantee success within any reasonable timeframe for higher-numbered puzzles.
