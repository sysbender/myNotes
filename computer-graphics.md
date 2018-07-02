


2D
 raster graphic
  vector graphic
  bitmaps = image
  textures - bitmap in 3d
  sprites - 2D object you can move around
  tiles -
  batching - draw many sprites with a single call
  texture atlasing -
  layering - z-buffering in 3D
  particls - VFX  visual effects , fire , smoke, dust, laser, water droplet, blood, crumbling objects
  shader -
  
programming in 2D
  D3D newer than openGL
  GLES - android, IOS
  ANGLE - desktop
  2D camera - 
  orthographic projection - glOrtho; 
  Left-handed coordinate system - DirectX ; 0,0 at upper left corner
  right-handed Coordinate system - openGL ; 0,0 at bottom left corner
  texture - bitmap images loaded onto the GPU, OpenGL not support; but SDL, SFML, GLFW support
  Texture creation - glGenTexture, glTexImage2D, glBindTexture, glTexParameter
  Drawing - 
    vertex buffer -  memory allocated on the GPU
      glGenBuffers, glBufferData      
    layout - postion , UV, color
      glVertexAttribPointer ; 
      (never use glGetAttribLocation) use glBindAttribLocation
     Draw - glDrawArrays
    primitive - triangle, line, quad(2 triangle)
    
    instancing - complex
    material - set of texture and shader used
    
    transparency 
    opaqueness
    texture atlasing - combine multiple image into a single texture
    particle emitter - size, velocity , acceleration, speed, color , lifetime
    particle system - 
    use interleave vbo - not multiple individu vbo
    
    
    
  
  
