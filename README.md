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

# 1. ProveedorService.java — agregar método buscarPorId

public Proveedor buscarPorId(Long id) {

    return proveedorRepository.findById(id).orElse(null);
    
}

# 2. ProveedorController.java 

@GetMapping("/{id}")

    public ResponseEntity<Proveedor> getProveedorPorId(@PathVariable Long id) {
    
        Proveedor proveedor = proveedorService.buscarPorId(id);
        
        if (proveedor == null) {
        
            return new ResponseEntity<>(HttpStatus.NOT_FOUND);
            
        }
        
        return new ResponseEntity<>(proveedor, HttpStatus.OK);
        
    }
