# 1. UsuarioService.java — agregar método buscarPorId

public Usuario buscarPorId(Long id) {

    return usuarioRepository.findById(id).orElse(null);
    
}

# 2. UsuarioController.java — agregar endpoint GET /{id}

@GetMapping("/{id}")

public ResponseEntity<Usuario> getUsuarioPorId(@PathVariable Long id) {

    Usuario usuario = usuarioService.buscarPorId(id);
    
    if (usuario == null) {
    
        return new ResponseEntity<>(HttpStatus.NOT_FOUND);
        
    }
    
    return new ResponseEntity<>(usuario, HttpStatus.OK);
    
}
