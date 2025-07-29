# Transformer Function

The **Transformer Function** is responsible for mapping and transforming data between two schemas.

It takes two parameters:

- `source_schema`: a list of dictionaries that define the **source** column names and types.
- `target_schema`: a list of dictionaries that define the **target** column names and types.

The function:
- Maps matching columns from `source_schema` to `target_schema` based on column name.
- Casts each value to the data type defined in the `target_schema`.
- Skips columns not present in `target_schema`.

---

## Example Transformer Logic

```python
from typing import List, Dict, Any

def transform_data(rows: List[Dict[str, Any]], source_schema: List[Dict[str, str]], target_schema: List[Dict[str, str]]) -> List[Dict[str, Any]]:
    """
    Transforms a list of rows from source schema to target schema, casting values to the target type.
    
    Parameters:
        rows: List of data rows (dictionaries).
        source_schema: List of source column definitions (e.g., [{'name': 'Quantity', 'type': 'str'}]).
        target_schema: List of target column definitions (e.g., [{'name': 'Quantity', 'type': 'int'}]).
    
    Returns:
        List of transformed rows.
    """
    type_casts = {
        'int': int,
        'float': float,
        'str': str,
        'bool': lambda x: str(x).lower() in ('true', '1', 'yes'),
    }

    # Build a lookup from target column name to type
    target_map = {col['name']: col['type'] for col in target_schema}

    transformed_rows = []

    for row in rows:
        new_row = {}
        for col_name, col_type in target_map.items():
            if col_name in row:
                try:
                    new_row[col_name] = type_casts[col_type](row[col_name])
                except Exception:
                    new_row[col_name] = None  # or handle default/fallback
            else:
                new_row[col_name] = None  # column not found in input row
        transformed_rows.append(new_row)

    return transformed_rows
