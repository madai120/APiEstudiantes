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

it('Debería permitir crear un nuevo estudiante', () => { cy.visit('/registro'); // URL del formulario de registro de estudiantes cy.get('input[name="nombre"]').type('Maria Alvarado'); cy.get('input[name="email"]').type('maria.alvarado@example.com'); cy.get('input[name="edad"]').type('22'); cy.get('input[name="curso"]').type('Matemáticas'); cy.get('button[type="submit"]').click(); cy.contains('Estudiante creado exitosamente').should('be.visible'); }); });

### Listar Estudiante

describe('Consulta de Estudiantes', () => {

it('Debería mostrar la lista de estudiantes registrados', () => { cy.visit('/estudiantes'); // URL de la lista de estudiantes cy.get('table').should('be.visible'); // Verifica que la tabla sea visible cy.get('table').find('tr').its('length').should('be.gt', 1); // Verifica que haya al menos un estudiante }); });

### Actualizar Estudiante

describe('Modificación de Información de Estudiantes', () => {

it('Debería permitir actualizar la información de un estudiante', () => { cy.visit('/estudiantes'); // URL de la lista de estudiantes cy.get('button.edit').first().click(); // Botón para editar el primer estudiante cy.get('input[name="nombre"]').clear().type('Maria Isabel Alvarado'); cy.get('input[name="curso"]').clear().type('Física'); cy.get('button[type="submit"]').click(); cy.contains('Información actualizada exitosamente').should('be.visible'); }); });

### Eliminar Estudiante

describe('Eliminación de Estudiantes', () => {

it('Debería permitir eliminar un estudiante', () => { cy.visit('/estudiantes'); // URL de la lista de estudiantes cy.get('button.delete').first().click(); // Botón para eliminar el primer estudiante cy.contains('Confirmar eliminación').click(); // Confirmación de eliminación cy.contains('Estudiante eliminado exitosamente').should('be.visible'); }); });

### Registrar pago de estudiante

describe('Gestión de Pagos de Estudiantes', () => {

it('Debería permitir registrar un pago para un estudiante', () => { cy.visit('/pagos/registro'); // URL del formulario de registro de pagos cy.get('select[name="estudiante"]').select('Maria Alvarado'); // Seleccionar estudiante cy.get('input[name="monto"]').type('150'); cy.get('input[name="fecha"]').type('2024-11-13'); cy.get('button[type="submit"]').click(); cy.contains('Pago registrado exitosamente').should('be.visible'); }); });

### Historia de pagos

describe('Consulta de Pagos de Estudiantes', () => {

it('Debería mostrar el historial de pagos de un estudiante', () => { cy.visit('/pagos'); // URL de la lista de pagos cy.get('table').should('be.visible'); // Verifica que la tabla de pagos sea visible cy.get('table').find('tr').its('length').should('be.gt', 1); // Verifica que haya al menos un pago registrado }); });

### Eliminar pago de estudiante

describe('Eliminación de Pagos de Estudiantes', () => {

it('Debería permitir eliminar un pago de un estudiante', () => { cy.visit('/pagos'); // URL de la lista de pagos cy.get('button.delete').first().click(); // Botón para eliminar el primer pago cy.contains('Confirmar eliminación').click(); // Confirmación de eliminación cy.contains('Pago eliminado exitosamente').should('be.visible'); }); });