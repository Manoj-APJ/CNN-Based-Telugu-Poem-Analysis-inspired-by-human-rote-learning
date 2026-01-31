# 🚀 Google Colab Training Guide

## Quick Start (5 Minutes Setup)

### Option 1: Direct Colab Link (Easiest)
1. Open this link in your browser:
   ```
   https://github.com/maneendra03/CNN-Based-Telugu-Poem-Analysis-inspired-by-human-rote-learning
   ```

2. Open the file: `Colab_Training_Setup.ipynb`

3. Click: **"Open in Colab"** button

4. Follow the notebook steps (they're numbered and color-coded)

---

### Option 2: Manual Upload to Colab
1. Download `Colab_Training_Setup.ipynb` to your computer
2. Go to: https://colab.research.google.com
3. Click: **File → Upload notebook**
4. Select the downloaded file
5. Run cells in order

---

## ⚙️ Before You Start

### ✅ Required
- Google account
- Google Drive (for saving results)
- Free Colab access OR Colab Pro ($10/month for faster GPU)

### ⏱️ Time Required
- **Setup**: 5 minutes
- **Download Data**: 10 minutes  
- **Training**: 2-3 hours (T4) or 1-1.5 hours (V100)
- **Total**: ~3-4 hours

### 💾 Space Required
- **RAM**: 8GB (Colab has 12GB)
- **Disk**: 3GB temporary + checkpoint size
- **GPU Memory**: 10GB (T4 has 16GB, good)

---

## 🔧 What the Notebook Does (Step by Step)

### Step 1: Setup Environment ✓
Checks GPU availability and mounts Google Drive

### Step 2: Clone Repository ✓
Pulls your project from GitHub:
```
https://github.com/maneendra03/CNN-Based-Telugu-Poem-Analysis-inspired-by-human-rote-learning
```

### Step 3: Install Dependencies ✓
Installs PyTorch, Transformers, and other required packages

### Step 4: Download Datasets ✓
Downloads 9,000+ Telugu poems from:
- HuggingFace: `SuryaKrishna02/aya-telugu-poems` (5,115 poems)
- Kaggle: `chandassu` (4,651 poems)

### Step 5: Train Model ✓
Trains the Enhanced Generator V3 with:
- 15 epochs
- Batch size: 8
- Learning rate: 0.001
- GPU acceleration

### Step 6: Evaluate Results ✓
Shows BLEU score, perplexity, and other metrics

### Step 7: Test Generation ✓
Generates sample poems with different prompts in Telugu

### Step 8: Save to Google Drive ✓
Saves:
- Evaluation results
- Model checkpoints (50-100 MB each)
- Training configuration

### Step 9: Create Report ✓
Generates a summary report of training

---

## 📊 Expected Results After Training

| Metric | Expected Value | Notes |
|--------|----------------|-------|
| BLEU Score | 0.35+ | Improvement from 0.15 |
| Perplexity | 8-12 | Lower is better |
| Repetition Rate | <10% | Down from 45% |
| Training Time | 2-3 hrs | On T4 GPU |
| Checkpoint Size | 50-100 MB | Save to Drive |

---

## 💡 Tips & Tricks

### ✅ For Faster Training
- **Use Colab Pro**: V100 GPU is 2-3x faster than T4
- **Reduce batch size**: Change 8 → 4 in Step 5
- **Use fewer epochs**: Change 15 → 5 for quick test

### ✅ For Better Results
- Run with **15+ epochs**
- Use **larger batch size** (8+)
- **Adjust learning rate** in config.yaml

### ✅ If Training Times Out
- Notebooks have 12-hour limit
- If approaching limit: Download checkpoint and restart
- Each training run is independent (can repeat)

### ✅ To Save Space
- Delete temporary files after step
- Only keep latest checkpoint
- Compress results before downloading

---

## 📥 After Training Completes

### Step 1: Download Results
```
Google Drive → telugu-poetry-training-results/
├── evaluation_results.json     ← BLEU, perplexity scores
├── validation_results.json     ← Test set metrics
├── training_report.json        ← Summary
├── config.yaml                 ← Hyperparameters used
└── checkpoint_model_*.pt       ← Trained model (50-100 MB)
```

### Step 2: Use Locally
```bash
cd "/Users/mani/Desktop/majorproject - A"

# Copy checkpoint from Google Drive
cp ~/Downloads/checkpoint_model_*.pt checkpoints/telugu/model_latest.pt

# Run UI with new model
python app/telugu_ui.py --checkpoint checkpoints/telugu/model_latest.pt
```

### Step 3: Push to GitHub (Optional)
```bash
git add -A
git commit -m "Add trained model checkpoint from Colab training"
git push origin main
```

---

## 🐛 Troubleshooting

### ❌ "GPU not available"
**Solution**: 
- Menu: **Runtime → Change runtime type**
- Select: **Hardware accelerator: GPU** (T4 or V100)
- Click: **Save**

### ❌ "Out of memory"
**Solution**:
- Reduce batch size: 8 → 4
- Reduce sequence length in config
- Clear GPU cache: `torch.cuda.empty_cache()`

### ❌ "Module not found"
**Solution**:
- Re-run Step 3 (Install Dependencies)
- Or restart kernel and run from beginning

### ❌ "Download failed"
**Solution**:
- Check internet connection
- Try again (servers sometimes slow)
- Step is optional - can skip and use cached data

### ❌ "Checkpoint not found"
**Solution**:
- Check if Step 5 completed (check output)
- Look in `checkpoints/telugu/` folder
- May not be saved if training interrupted

---

## 📞 Need Help?

### Check These Files
1. **`PROJECT_STATUS.md`** - Current project status
2. **`DOCUMENTATION.md`** - Technical details
3. **`COMPLETION_ANALYSIS.md`** - What's done/remaining

### Run Validation
In Colab, add a cell:
```python
import subprocess
result = subprocess.run(
    ["python", "tests/comprehensive_validation.py"],
    capture_output=True, text=True
)
print(result.stdout)
```

### Check Logs
After each step, scroll up to see detailed logs

---

## 🎉 Success!

Once training completes:
1. ✅ You have a trained Telugu poetry model
2. ✅ Results are saved to Google Drive
3. ✅ Checkpoint can be used locally
4. ✅ Ready for project defense/submission

---

## 📌 Important Notes

- **Each Colab session timeout**: 12 hours (plenty for this)
- **GPU free quota**: ~40-50 hours/month (enough for multiple runs)
- **Colab storage**: Temporary (files deleted after session)
- **Google Drive storage**: Permanent (keep your results!)

---

**Created**: January 31, 2026  
**GitHub**: https://github.com/maneendra03/CNN-Based-Telugu-Poem-Analysis-inspired-by-human-rote-learning  
**Project**: CNN-Based Telugu Poetry Generation
