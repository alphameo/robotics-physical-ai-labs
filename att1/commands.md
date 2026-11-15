# Стандартные команды

## Управление контейнером

```bash
./scripts/run_container.sh --cpu
```

```bash
./scripts/kill_container.sh
```

```bash
docker exec -it mujoco-sim-cpu bash
```

## Запуск симуляции с мануальным управлением

```bash
python3 panda_teleop.py
```

## Инференс

```bash
python3 inference.py --checkpoint logs/PandaPickCube_20261009_101235/model_1000.pt
```

```bash
python3 inference.py --checkpoint logs/PandaPickCube_20261009_101235/model_1000.pt \
    --record logs/PandaPickCube_20261009_101235/video_iter1000.mp4 --episodes 3
```

### Эксперименты

#### In-domain

```bash
python3 inference.py --checkpoint logs/PandaPickCube_20261009_101235/model_1000.pt \
    --record logs/PandaPickCube_20261009_101235/exp1_indomain.mp4 --episodes 10
```

#### Отдаление

Стандартная позиция куба: $(0; 0.5)$,

Безопасный диапазон: $(\pm 0.3; \pm 0.3)$

```bash
python3 inference.py --checkpoint logs/PandaPickCube_20261009_101235/model_1000.pt \
    --cube_x 0.15 --cube_y 0.1 \
    --record logs/PandaPickCube_20261009_101235/exp2_far_015x01.mp4 \
    --episodes 10
```

#### Шум

```bash
python3 inference.py --checkpoint logs/PandaPickCube_20261009_101235/model_1000.pt \
    --obs_noise 0.02 \
    --record logs/PandaPickCube_20261009_101235/exp3_noise_002.mp4 --episodes 10
```
