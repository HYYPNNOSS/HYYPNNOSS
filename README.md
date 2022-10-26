<p align="center">
  <img src="https://github.com/HYYPNNOSS/HYYPNNOSS/blob/main/1027f80aeabcbb74a2e698be71829e9e.gif" alt="batmam hhh" width="250" height="250" />
</p>
<br>
<br>
<p align="center" style="wordspac"> 𝐌𝐄𝐃𝐔𝐒𝐀 : 𝕄𝔼&nbsp;&nbsp;&nbsp;&nbsp;𝐏𝐎𝐒𝐄𝐈𝐃𝐎𝐍 : <img width="30px" align="left" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" /> </p>









<h3 align="center"> 𝟜𝟚 𝕡𝕣𝕠𝕗𝕚𝕝𝕖: </h3>
<br>
<p align="center">
<img src="https://badge42.vercel.app/api/v2/cl2i5l5rv000609mjmb5tsx1l/stats?cursusId=21&coalitionId=74">
  </p>

```c
#include <mlx.h>
#include <math.h>
//math function: "y=x^{\frac{2}{3}}+0.9*\sqrt{3.3\ -\ x^{2}}*\sin(a*\pi*x)\"

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
    double x = 500;
    double tmp_x;
    double a = 10000;
    double y;
    mlx = mlx_init();
    mlx_win = mlx_new_window(mlx, 1920, 1080, "Hello world!");
    img.img = mlx_new_image(mlx, 1920, 1080);
    img.addr = mlx_get_data_addr(img.img, &img.bits_per_pixel, &img.line_length,
                                &img.endian);

double yy;
double yyy;
double yyyy;
    while (x < 1000)
    {
        tmp_x = map(x, 500, 1000, 1.8164, -1.8164);
        y = 0;
        yy = cbrt(pow(tmp_x, 2));
        yyy = 0.9 * sqrt(3.3 - pow(tmp_x, 2));
        yyyy = sin(a * M_PI * tmp_x);
        y = yy + yyy * yyyy;
        my_mlx_pixel_put(&img, x, map(y, 1.8164, -1.8164, 500, 1000), 0x002b1d69);
        x= x + 0.0001 ;
    }
    mlx_put_image_to_window(mlx, mlx_win, img.img, 0, 0);
    mlx_loop(mlx);
}
```
