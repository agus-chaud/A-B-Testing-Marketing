# Tests (TDD)

Estructura para pruebas unitarias e integracion.

## Convenciones

- Usar `pytest` o `unittest` segun preferencia del proyecto.
- Nombrar tests: `test_<modulo>_<funcion>.py` o `test_<modulo>.py`.
- Cada spec debe tener criterios de aceptacion verificables mediante tests.

## Ejecucion

```bash
# Con pytest
pytest tests/ -v

# Con unittest
python -m unittest discover tests/ -v
```

## Ejemplo minimo

```python
# tests/test_sample.py
def test_placeholder():
    """Placeholder para validar que el directorio de tests esta operativo."""
    assert True
```
