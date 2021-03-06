# sdl2_window [![Build Status](https://travis-ci.org/PistonDevelopers/sdl2_window.svg?branch=master)](https://travis-ci.org/PistonDevelopers/sdl2_window)

An SDL2 back-end for the Piston game engine

Maintainers: @TyOverby, @bvssvni, @Coeuvre

[How to contribute](https://github.com/PistonDevelopers/piston/blob/master/CONTRIBUTING.md)

### How to create a window

```Rust
let mut window = Sdl2Window::new(
    shader_version::opengl::OpenGL_3_2,
    WindowSettings {
        title: "My application".to_string(),
        size: [640, 480],
        fullscreen: false,
        exit_on_esc: true,
        samples: 4,
    }
);
```

### How to set up Gfx

After you have created a window, do the following:

```Rust
let mut device = gfx::GlDevice::new(|s| unsafe {
    transmute(sdl2::video::gl_get_proc_address(s))
});
let (w, h) = window.get_size();
let frame = gfx::Frame::new(w as u16, h as u16);
```

### Troubleshooting

* [I get `ld: library not found for -lSDL2` error on OSX](https://github.com/PistonDevelopers/rust-empty/issues/175)

## Dependencies

![dependencies](./Cargo.png)

