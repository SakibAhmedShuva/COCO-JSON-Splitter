# COCO JSON Splitter

A Python utility for splitting COCO-formatted datasets into training, validation, and test sets. This tool is particularly useful for handling COCO JSON files exported from CVAT (Computer Vision Annotation Tool) and preparing them for machine learning tasks.

## Features

- Split COCO dataset into train, validation, and test sets with customizable ratios
- Maintains all COCO format properties (annotations, categories, info, licenses)
- Supports both binary (train/val) and three-way (train/val/test) splits
- Automatically organizes images and annotations in the output directory
- Compatible with COCO JSON files exported from CVAT
- Preserves image-annotation relationships during splitting

## Prerequisites

- Python 3.6 or higher
- Required Python packages:
  - scikit-learn
  - json
  - shutil

## Installation

1. Clone the repository:
```bash
git clone https://github.com/your-username/coco-json-splitter.git
cd coco-json-splitter
```

2. Install required packages:
```bash
pip install scikit-learn
```

## Usage

open coco_splitter.ipynb

```python

# Define your paths
coco_json_path = 'path/to/your/coco/annotations.json'
image_dir = 'path/to/your/images'
output_dir = 'path/to/output/directory'

# Split the dataset
split_coco_dataset(
    coco_json_path=coco_json_path,
    image_dir=image_dir,
    output_dir=output_dir,
    train_split=0.8,
    val_split=0.2,
    test_split=0.0  # Set to 0 for binary split
)
```

### Parameters

- `coco_json_path`: Path to the COCO JSON file (exported from CVAT)
- `image_dir`: Directory containing the source images
- `output_dir`: Directory where split datasets will be saved
- `train_split`: Proportion of data for training (default: 0.7)
- `val_split`: Proportion of data for validation (default: 0.2)
- `test_split`: Proportion of data for testing (default: 0.1)

### Output Structure

```
output_dir/
├── train/
│   ├── images/
│   └── instances_train.json
├── val/
│   ├── images/
│   └── instances_val.json
└── test/  (if test_split > 0)
    ├── images/
    └── instances_test.json
```

## Example

```python
# Example with binary split (80% train, 20% validation)
split_coco_dataset(
    coco_json_path='annotations/instances_default.json',
    image_dir='images',
    output_dir='split_dataset',
    train_split=0.8,
    val_split=0.2,
    test_split=0.0
)
```

## Notes

- Ensure your COCO JSON file follows the standard COCO format
- The script automatically handles CVAT-exported COCO JSON files
- Split ratios must sum to 1.0
- Random seed is set to 42 for reproducibility
- Missing images will generate warnings but won't stop the process

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

For more projects, visit: https://github.com/SakibAhmedShuva
