# EXAMEN FINAL
## API DE ESTUDIANTES
### Estructura

    Api_Estudiante
    cypress
    Integracion
    Crear estidiant_spec.js
    Listar estidiant_spec.js
    Actualizar estidiant_spec.js
    Eliminar estidiant_spec.js
    Cypress.json
    README.md

### Ejecucion de prueba
Herramientas instaladas

    Node.js
    npm

Instricciones

npm install
npx cypress open
npx cypress run

## Prueba de cypress
### Crear Estudiantes

describe('Gestión de Estudiantes', () => {

it('Debería permitir crear un nuevo estudiante', () => { cy.visit('/registro'); // URL del formulario de registro de estudiantes cy.get('input[name="nombre"]').type('Madaì Cuc'); cy.get('input[name="email"]').type('madai@example.com'); cy.get('input[name="edad"]').type('22'); cy.get('input[name="curso"]').type('Matemáticas'); cy.get('button[type="submit"]').click(); cy.contains('Estudiante creado exitosamente').should('be.visible'); }); });

### Listar Estudiante

describe('Consulta de Estudiantes', () => {

it('Debería mostrar la lista de estudiantes registrados', () => { cy.visit('/estudiantes'); // URL de la lista de estudiantes cy.get('table').should('be.visible'); // Verifica que la tabla sea visible cy.get('table').find('tr').its('length').should('be.gt', 1); // Verifica que haya al menos un estudiante }); });

### Actualizar Estudiante

describe('Modificación de Información de Estudiantes', () => {

it('Debería permitir actualizar la información de un estudiante', () => { cy.visit('/estudiantes'); // URL de la lista de estudiantes cy.get('button.edit').first().click(); // Botón para editar el primer estudiante cy.get('input[name="nombre"]').clear().type('Madaì Cuc'); cy.get('input[name="curso"]').clear().type('Física'); cy.get('button[type="submit"]').click(); cy.contains('Información actualizada exitosamente').should('be.visible'); }); });

### Eliminar Estudiante

describe('Eliminación de Estudiantes', () => {

it('Debería permitir eliminar un estudiante', () => { cy.visit('/estudiantes'); // URL de la lista de estudiantes cy.get('button.delete').first().click(); // Botón para eliminar el primer estudiante cy.contains('Confirmar eliminación').click(); // Confirmación de eliminación cy.contains('Estudiante eliminado exitosamente').should('be.visible'); }); });

