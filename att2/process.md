# Help

Notebook does not run?

- Clear all flags for `pip`
- Set version for playground: `%pip install "playground[learning]==0.2.0"`

## Params

```python
print(manipulation_params.rsl_rl_config("PandaPickCube").to_dict())
```

```python
print(f"gripper_box={env_cfg.reward_config.scales.gripper_box}")
# raw_env = registry.load(ENV_NAME, config=env_cfg)
```

```python
# cfg_dict["save_interval"] = args.save_interval
print(f"learning_rate={cfg_dict['algorithm']['learning_rate']}")
```

## Experiments

| Картина                               | Интерпретация                                                  |
| ------------------------------------- | -------------------------------------------------------------- |
| Плато на высоком уровне, SR ≈ 8–10/10 | Политика научилась хорошо выполнять задачу и стабилизировалась |
| Плато на низком уровне                | Обучение застряло (редко для baseline)                         |
| Кривая ещё растёт к концу             | Обучение не вышло на плато; возможно, стоит продлить           |
| Резкие колебания без тренда           | Возможно, слишком большой `learning_rate`                      |

```bash
python3 inference.py --checkpoint logs/baseline/model_1000.pt \
    --record logs/baseline/video.mp4 --episodes 10
```
