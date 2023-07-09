<?php
class graphql{
public static function buildGraphQLQuery($operations)
    {
        $query = '';

        foreach ($operations as $operationName => $operationData) {
            $fields = $operationData['fields'];
            $arguments = $operationData['arguments'] ?? [];

            $operationQuery = "{$operationName}";

            if (!empty($arguments)) {
                $argumentsString = '';

                foreach ($arguments as $key => $value) {
                    if (is_array($value)) {
                        $value = json_encode($value);
                    }
                    $argumentsString .= "{$key}: {$value}, ";
                }

                $argumentsString = rtrim($argumentsString, ', ');
                $operationQuery .= " ({$argumentsString})";
            }

            $operationQuery .= " {";

            foreach ($fields as $field => $nestedFields) {
                if (is_array($nestedFields)) {
                    $nestedFieldsString = '';

                    foreach ($nestedFields as $nestedField) {
                        $nestedFieldsString .= " {$nestedField}";
                    }

                    $operationQuery .= " {$field}{{$nestedFieldsString}}";
                } else {
                    $operationQuery .= " {$nestedFields}";
                }
            }

            $operationQuery .= " }";

            $query .= "{$operationQuery}\n";
        }

        return "query {\n{$query}}";

    }
}
}
