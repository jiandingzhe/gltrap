If you use vertex array objects, you must not bind vertex buffers prior to it. Some driver will work, but some will just silently not output anything.

    // you die
    glBindBuffer(GL_ARRAY_BUFFER, vbo);
    glBindVertexArray(vao);

    // this is OK, but the VBO binding is useless
    glBindVertexArray(vao);
    glBindBuffer(GL_ARRAY_BUFFER, vbo);
