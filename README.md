**42 Student**
<br>
<img src="https://badge42.vercel.app/api/v2/cl2i5l5rv000609mjmb5tsx1l/stats?cursusId=21&coalitionId=74">

```c
#include <mlx.h>
#include <math.h>

typedef struct    s_data {
    void    *img;
    char    *addr;
    int        bits_per_pixel;
    int        line_length;
    int        endian;
}                t_data;

void    my_mlx_pixel_put(t_data *data, int x, int y, int color)
{
    char    *dst;

    dst = data->addr + (y * data->line_length + x * (data->bits_per_pixel / 8));
    *(unsigned int*)dst = color;
}

double map(double x, double in_min, double in_max, double out_min, double out_max)
{
  return (x - in_min) * (out_max - out_min) / (in_max - in_min) + out_min;
}

int    main(void)
{
    void    *mlx;
    void    *mlx_win;
    t_data    img;
    int x = 500;
    double tmp_x;
    int a = 100;
    double y;
    mlx = mlx_init();
    mlx_win = mlx_new_window(mlx, 1920, 1080, "Hello world!");
    img.img = mlx_new_image(mlx, 1920, 1080);
    img.addr = mlx_get_data_addr(img.img, &img.bits_per_pixel, &img.line_length,
                                &img.endian);

    while (x < 1000)
    {
        tmp_x = map(x, 500, 1000, -2, 2);
        y = cbrt(pow(tmp_x, 2)) + 0.9 * sqrt(3.3 - pow(tmp_x, 2)) * sin(a * M_PI * tmp_x);
        my_mlx_pixel_put(&img, x, map(y, 2, -2, 500, 1000), 0x00FF0000);
        x++;
    }
    mlx_put_image_to_window(mlx, mlx_win, img.img, 0, 0);
    mlx_loop(mlx);
}

```
