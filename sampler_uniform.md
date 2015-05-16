In GLSL, although the texture uniform types - such as sampler2D, sampler 3D, samplerCube - are named with "sampler", they have nothing to do with host side sampler objects, and the uniform value should be set with index of texture units.

This is wrong:

    GLuint sampler_obj = 0;
    glGenSamplers(1, &sampler_obj);
    ......
    glActiveTexture(GL_TEXTURE0);
    glUniform1i(location, sampler_obj);

This is correct:

    glActiveTexture(GL_TEXTURE0);
    glUniform1i(location_a, 0);
    ......
    glActiveTexture(GL_TEXTURE1);
    glUniform1i(location_b, 1);
    ......
    glActiveTexture(GL_TEXTURE2);
    glUniform1i(location_c, 2);
    ......
    
