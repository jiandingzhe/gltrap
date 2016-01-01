When we bind VAO or EBO, then unbinding it after we never use them is a good practise.But we must be careful about the unbind order.

This is wrong:
  glBindVertexArray(VAO)
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
...
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, 0);
glBindVertexArray(0);
...
glBindVertexArray(VAO);
glDrawElements(GL_TRIANGLES, indices.size(), GL_UNSIGNED_INT, 0);//crash

This is correct:
glBindVertexArray(VAO)
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
...
glBindVertexArray(0);
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, 0);
...
glBindVertexArray(VAO);
glDrawElements(GL_TRIANGLES, indices.size(), GL_UNSIGNED_INT, 0);//don't crash
