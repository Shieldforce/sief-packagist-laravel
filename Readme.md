# SIEF - Pacote de Funcionalidades

### Instalação - Passo a Passo

- Instalar o Git (Link no rodapé).
- Instalar o Composer (Link no rodapé).
- Rodar o comando: "composer require shieldforce/sief-packagist-laravel dev-master"

### Primeiro pacote é o AutoValidation, Segue instruções de Uso
### ==============================Início de instrução de uso do AutoValidation===============================

### Exemplo de Uso no Model, com a Trait (Nesse caso a Trait Já contém o método boot o o ObserverValidation) :

    /**
     * Start ObserverValidation
     * Method (Optional) for Trait
     */
    use TraitStartValidation;
    
    /**
     * @var array
     * These are the classes that intercept the laravel action functions
     */
    public static $rules =
        [
            'creating'        => [],
            'updating'        =>
                [
                    'edi_ano' => ['required', 'integer', 'max:2050', 'min:2000']
                ],
            'saving'          => [],
            'deleting'        => [],
            'restoring'       => [],
        ];
        
### Exemplo de Uso no Model, com o Método boot() (Nesse caso o método boot é chamado direto no Model) :

    /**
     * Method boot is Model
     * Start Validation (self::observe(new ObserverValidation))
     */
    protected static function boot()
    {
        parent::boot();
        self::observe(new ObserverValidation);
    }
    
    /**
     * @var array
     * These are the classes that intercept the laravel action functions
     */
    public static $rules =
        [
            'creating'        => [],
            'updating'        =>
                [
                    'edi_ano' => ['required', 'integer', 'max:2050', 'min:2000']
                ],
            'saving'          => [],
            'deleting'        => [],
            'restoring'       => [],
        ];
        
### No arquivo resources/lang/pt_BR/validation.php podemos configurar as mensagens de retorno, trocar nomes de atributos, etc...:

    return [
    
        /*
        |--------------------------------------------------------------------------
        | Validation Language Lines
        |--------------------------------------------------------------------------
        |
        | The following language lines contain the default error messages used by
        | the validator class. Some of these rules have multiple versions such
        | as the size rules. Feel free to tweak each of these messages here.
        |
        */
    
        // recaptcha - Guilherme Ferro
        'recaptcha' => 'O campo :attribute não está correto.',
    
        'accepted'             => 'O :attribute deve ser aceito.',
        'active_url'           => 'O :attribute não é uma URL válida.',
        'after'                => 'O :attribute deve ser uma data depois :date.',
        'alpha'                => 'O :attribute só podem conter letras.',
        'alpha_dash'           => 'O :attribute só podem conter letras, números e traços.',
        'alpha_num'            => 'O :attribute só pode conter letras e números.',
        'array'                => 'O :attribute deve ser uma matriz.',
        'before'               => 'O :attribute deve ser uma data antes :date.',
        'between'              => [
            'numeric' => 'O :attribute deve situar-se entre :min e :max.',
            'file'    => 'O :attribute deve situar-se entre :min e :max kilobytes.',
            'string'  => 'O :attribute deve situar-se entre :min e :max characters.',
            'array'   => 'O :attribute deve ter entre :min e :max itens.',
        ],
        'boolean'              => 'O :attribute campo deve ser verdadeira ou falsa.',
        'confirmed'            => 'O :attribute confirmação não corresponde.',
        'date'                 => 'O :attribute não é uma data válida.',
        'date_format'          => 'O :attribute não coincide com o formato :format.',
        'different'            => 'O :attribute e :other deve ser diferente.',
        'digits'               => 'O :attribute deve ser :digits dígitos.',
        'digits_between'       => 'O :attribute deve situar-se entre :min e :max dígitos.',
        'dimensions'           => 'O :attribute tem dimensões de imagem inválidos.',
        'distinct'             => 'O :attribute campo tem um valor duplicado.',
        'email'                => 'O :attribute deve ser um endereço de e-mail válido.',
        'exists'               => 'O selecionado :attribute é inválido.',
        'filled'               => 'O :attribute campo é obrigatório.',
        'image'                => 'O :attribute deve ser uma imagem.',
        'in'                   => 'O selecionado :attribute é inválido.',
        'in_array'             => 'O :attribute campo não existe no :other.',
        'integer'              => 'O :attribute deve ser um número inteiro.',
        'ip'                   => 'O :attribute deve ser um endereço IP válido.',
        'json'                 => 'O :attribute deve ser uma cadeia JSON válido.',
        'max'                  => [
            'numeric' => 'O :attribute não pode ser superior a :max.',
            'file'    => 'O :attribute não pode ser superior a :max kilobytes.',
            'string'  => 'O :attribute não pode ser superior a :max characters.',
            'array'   => 'O :attribute não pode ter mais de :max itens.',
        ],
        'mimes'                => 'O :attribute deve ser um arquivo do tipo: :values.',
        'min'                  => [
            'numeric' => 'O :attribute deve ser de pelo menos :min.',
            'file'    => 'O :attribute deve ser de pelo menos :min kilobytes.',
            'string'  => 'O :attribute deve ser de pelo menos :min characters.',
            'array'   => 'O :attribute deve ter pelo menos :min itens.',
        ],
        'not_in'               => 'O selecionado :attribute é inválido.',
        'numeric'              => 'O :attribute deve ser um número.',
        'present'              => 'O campo :attribute deve estar presente.',
        'regex'                => 'O :attribute formato é inválido.',
        'required'             => 'O campo :attribute é necessário.',
        'required_if'          => 'O campo :attribute é necessária quando :other é :value.',
        'required_unless'      => 'O campo :attribute é necessária a menos :other é in :values.',
        'required_with'        => 'O campo :attribute é necessária quando :values é present.',
        'required_with_all'    => 'O campo :attribute é necessária quando :values é present.',
        'required_without'     => 'O campo :attribute é necessária quando :values não está presente.',
        'required_without_all' => 'O campo :attribute é requerido quando nenhum :values estão presentes.',
        'same'                 => 'O :attribute e :other devem corresponder.',
        'size'                 => [
            'numeric' => 'O :attribute deve ser :size.',
            'file'    => 'O :attribute deve ser :size kilobytes.',
            'string'  => 'O :attribute deve ser :size characters.',
            'array'   => 'O :attribute deve conter :size itens.',
        ],
        'string'               => 'O :attribute deve ser uma string.',
        'timezone'             => 'O :attribute deve ser uma zona válida.',
        'unique'               => 'Este :attribute já foi registrado.',
        'url'                  => 'O :attribute formato é inválido.',
    
        /*
        |--------------------------------------------------------------------------
        | Custom Validation Language Lines
        |--------------------------------------------------------------------------
        |
        | Here you may specify custom validation messages for attributes using the
        | convention "attribute.rule" to name the lines. This makes it quick to
        | specify a specific custom language line for a given attribute rule.
        |
        */
    
        'custom' => [
                'attribute-name' => [
                    'rule-name' => 'custom-message',
                ],
                'edi_id' => [
                    'required'                            => 'Campo :attribute é obrigatório',
                    'integer'                             => 'Campo :attribute deve ser um inteiro',
                    'min'                                 => 'Campo :attribute deve conter a data mínima de 2000',
                    'max'                                 => 'Campo :attribute deve conter a data máxima de 2050',
                ],
            ],
    
        /*
        |--------------------------------------------------------------------------
        | Custom Validation Attributes
        |--------------------------------------------------------------------------
        |
        | The following language lines are used to swap attribute place-holders
        | with something more reader friendly such as E-Mail Address instead
        | of "email". This simply helps us make messages a little cleaner.
        |
        */
    
        'attributes' => [
                'g-recaptcha-response'                 => 'reCAPTCHA',
                'edi_id'                               => 'Identificação da Edição',
            ],
    
    ];
    
### No caso do retorno de erros de validação é sempre retornado esse modelo:

    return back()
        ->with('error', 'Validação de Campos não passou!!')
        ->withErrors($validator)
        ->withInput()
        ->throwResponse();
        
### ==============================Fim de instrução de uso do AutoValidation===============================


### Tecnologias utilizadas
- Git (https://git-scm.com/)
- Composer (https://getcomposer.org/download/)